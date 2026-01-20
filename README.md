# Django-D2
Proyecto educativo
## Tutorial paso a paso: crear proyecto Django + repo GitHub (con templates)

> Objetivo: dejar un proyecto Django listo, versionado en GitHub, con app `configuracion` y carpeta `templates` configurada en `settings.py`.

---

### 1) Crear repo en GitHub (con README y .gitignore)

1. En GitHub → **New repository**
2. Nombre sugerido: `entorno-config-django`
3. Marca:

   * ✅ **Add a README file**
   * ✅ **Add .gitignore** → elige **Python**
4. Create repository

---

### 2) Clonar el repositorio en tu PC

En tu carpeta de trabajo (por ejemplo `D:\PROYECTOS`), abre **CMD** o **Git Bash** y ejecuta:

```bash
git clone https://github.com/TU_USUARIO/entorno-config-django.git
cd entorno-config-django
```

---

### 3) Crear entorno virtual y activarlo

En **CMD** (Windows), dentro del repo:

```bat
python -m venv venv
venv\Scripts\activate
```

Si se activó bien, verás algo como `(venv)` al inicio de la línea.

---

### 4) Instalar Django (y actualizar pip)

```bat
python -m pip install --upgrade pip
pip install django
```

Para verificar:

```bat
django-admin --version
```

---

### 5) Crear el proyecto Django

Crea el proyecto dentro del repo:

```bat
django-admin startproject entorno_config_django
```

Te quedará una carpeta `entorno_config_django/` dentro del repo.

---

### 6) Entrar a la carpeta del proyecto

```bat
cd entorno_config_django
```

---

### 7) Crear la app `configuracion`

```bat
python manage.py startapp configuracion
```

---

### 8) Ejecutar migraciones iniciales

```bat
python manage.py migrate
```

---

### 9) Registrar la app en `INSTALLED_APPS`

Abre:

`entorno_config_django/settings.py`

Busca `INSTALLED_APPS` y agrega `'configuracion',` al final (como tú lo indicaste):

```py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'configuracion',
]
```

---

### 10) Configurar carpeta global `templates`

1. **Crea la carpeta** `templates` en la raíz del proyecto (al mismo nivel que `manage.py`).

Tu estructura típica queda así:

```
entorno-config-django/
  venv/
  entorno_config_django/
    manage.py
    templates/
    configuracion/
    entorno_config_django/
      settings.py
      urls.py
      wsgi.py
      asgi.py
```

2. En `settings.py`, busca `TEMPLATES` y cambia `DIRS` a:

```py
'DIRS': [BASE_DIR / 'templates'],
```

Quedará parecido a esto:

```py
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [BASE_DIR / 'templates'],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

---

## Bonus recomendado (para que quede “redondo”)

### A) Probar el servidor

```bat
python manage.py runserver
```

Abre: `http://127.0.0.1:8000/`

### B) Guardar cambios en Git y subir

Vuelve a la raíz del repo (si estás adentro de la carpeta del proyecto, sube un nivel):

```bat
cd ..
git status
git add .
git commit -m "Init Django project + app configuracion + templates DIRS"
git push
```

