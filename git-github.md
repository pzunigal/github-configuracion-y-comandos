# Fundamentos de GIT: Configuración y Comandos Básicos
![Git Banner](github-banner.png)
## 1. Configuración inicial
Configura identidad y preferencias globales o por repositorio.

- Identidad:
```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@correo.com"
```
- Editor y color:
```bash
git config --global core.editor "code --wait"
git config --global color.ui auto
```
- Ver configuración:
```bash
git config --list
git config --global --edit
```

## 2. Claves SSH y credenciales
- Generar clave SSH:
```bash
ssh-keygen -t ed25519 -C "tu@correo.com"
# luego agregar ~/.ssh/id_ed25519.pub al servicio (GitHub/GitLab)
```
- Cache de credenciales (ej. macOS/Windows/Linux):
```bash
git config --global credential.helper osxkeychain    # macOS
git config --global credential.helper wincred         # Windows
git config --global credential.helper cache           # Linux (temporal)
```

## 3. Iniciar y clonar repositorios
- Nuevo repo:
```bash
git init
```
- Clonar:
```bash
git clone git@github.com:usuario/repo.git
```

## 4. Flujo básico de trabajo
- Estado y archivos:
```bash
git status
git add archivo.txt        # añadir archivo al staging
git add .                  # añadir todos
```
- Confirmar cambios:
```bash
git commit -m "Mensaje claro"
git commit -am "Cambio en tracked files"  # añadir y commitear cambios en archivos ya trackeados
```
- Ver historial:
```bash
git log --oneline --graph --decorate
git show <commit>
```

## 5. Ramas (branches)
- Crear y cambiar:
```bash
git branch nueva-rama
git switch nueva-rama       # o: git checkout -b nueva-rama
```
- Listar:
```bash
git branch --all
```
- Merge:
```bash
git switch main
git merge nueva-rama
```
- Eliminar/renombrar:
```bash
git branch -d antigua-rama
git branch -m nombre-viejo nombre-nuevo
```

## 6. Sincronizar con remoto
- Ver remotos:
```bash
git remote -v
```
- Añadir remoto:
```bash
git remote add origin git@github.com:usuario/repo.git
```
- Traer y fusionar:
```bash
git fetch origin
git pull origin main    # fetch + merge
```
- Enviar:
```bash
git push origin main
git push -u origin nueva-rama  # establecer upstream
```

## 7. Deshacer y recuperación
- Deshacer staged:
```bash
git restore --staged archivo.txt
```
- Deshacer cambios en working tree:
```bash
git restore archivo.txt
```
- Reset (cuidado):
```bash
git reset --soft HEAD~1   # deshace commit, mantiene cambios en staged
git reset --mixed HEAD~1  # default, mantiene en working dir
git reset --hard HEAD~1   # destruye cambios
```
- Revertir commit público:
```bash
git revert <commit>
```
- Reflog (recuperar commits perdidos):
```bash
git reflog
```

## 8. Stash
- Guardar cambios temporales:
```bash
git stash
git stash save "mensaje"
git stash list
git stash apply stash@{0}
git stash pop
```

## 9. Comparaciones y diferencias
- Diferencias:
```bash
git diff                # working vs staged
git diff --staged       # staged vs last commit
git diff HEAD~1..HEAD   # comparar commits
```

## 10. Etiquetas (tags)
- Crear y listar:
```bash
git tag v1.0.0
git tag -a v1.0.0 -m "Lanzamiento v1.0.0"
git push origin v1.0.0
```

## 11. .gitignore
- Ignorar archivos agregando patrones en `.gitignore`.
- Para dejar de trackear un archivo ya comiteado:
```bash
git rm --cached archivo
```

## Buenas prácticas rápidas
- Mensajes de commit claros y en presente.
- Hacer commits pequeños y atómicos.
- Mantener rama main estable; trabajar en feature branches.
- Revisar `git status` y `git log` frecuentemente.

Referencias rápidas:
- git help <comando>
- https://git-scm.com/docs
