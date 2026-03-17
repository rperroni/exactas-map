# FCEFYN-Map

Mapa interactivo de materias y sus correlativas para los planes de estudio de la Facultad de Ciencias Exactas, Físicas y Naturales.

Inspirado fuertemente en el proyecto [FIUBA-Map](https://github.com/fdelmazo/FIUBA-Map).

---

## Tabla de contenidos

- [Introducción](#introducción)  
- [Características principales](#características-principales)  
- [Capturas / Demo](#capturas--demo)  
- [Cómo usar](#cómo-usar)  
- [Configuración de Firebase](#configuración-de-firebase)  
- [Pendientes / TODO](#pendientes--todo)  
- [Cómo contribuir](#cómo-contribuir)  
- [Licencia](#licencia)  
- [Agradecimientos](#agradecimientos)

---

## Introducción

**FCEFYN-Map** es una herramienta web que permite visualizar **interactivamente** los planes de estudio de la Facultad de Ciencias Exactas, Físicas y Naturales (FCEFyN) de la Universidad Nacional de Córdoba (UNC).  

Facilita ver las correlativas de cada materia, seleccionarlas como cursadas o aprobadas, y planificar el progreso académico.  

El diseño y enfoque se inspiran en [FIUBA-Map](https://github.com/fdelmazo/FIUBA-Map), que realizó una idea similar para la Facultad de Ingeniería de la Universidad de Buenos Aires.

---

## Características principales

- Visualización clara de materias y correlativas por carrera y plan de estudios  
- Interfaz interactiva para marcar materias aprobadas y pendientes  
- Navegación por carrera y plan específicos  
- Sincronización en la nube con Firebase (Firestore): tu progreso se guarda y se comparte entre dispositivos  
- *(Opcional: tracking de créditos, etc.)*  

---

## Capturas / Demo

<div style="display: flex; gap: 16px; align-items: flex-start;">
  <img src="/assets/img/captura_escritorio.png" alt="Captura escritorio" style="height: 340px; border:1px solid #ccc;">
  <img src="/assets/img/captura_mobile.jpeg" alt="Captura móvil" style="height: 340px; border:1px solid #ccc;">
</div>

---

## Cómo usar

1. Cloná el repositorio:
   ```bash
   git clone https://github.com/rperroni/fcefyn-map.git
   cd fcefyn-map
   ```
2. Abrí `index.html` en tu navegador.  
   - Si tu navegador bloquea módulos ES desde file://, serví el proyecto con un servidor local:
     ```bash
     npx serve .
     # o
     python3 -m http.server 8080
     ```
3. Para sincronizar tu progreso en la nube:
   - Ingresá tu DNI en el campo “DNI para sincronizar” y presioná “Sincronizar”.  
   - Presioná “Local” para volver a usar solo almacenamiento local del navegador.
4. Si no tenés que cambiar nada de Firebase, no necesitás backend ni variables de entorno.

---

## Configuración de Firebase

Esta app usa Firebase cargado por script (CDN) y Firestore como base de datos. No requiere backend.

- Dónde se configura:
  - index.html incluye los scripts de Firebase.
  - script.js contiene el objeto `firebaseConfig` y la inicialización de Firestore.
- Para usar tu propio proyecto (forks):
  1. Creá un proyecto en Firebase y habilitá Firestore en modo producción.
  2. Agregá tu dominio/localhost en “Authentication -> Settings -> Authorized domains” (aunque no uses auth, evita bloqueos de origen).
  3. Reemplazá el `firebaseConfig` en `script.js` con tus credenciales del panel de Firebase.
  4. Revisá y ajustá tus reglas de seguridad de Firestore para permitir solo los accesos deseados.
- Notas:
  - Si la sincronización falla, la app sigue funcionando en modo local.
  - El DNI se usa como ID de documento en la colección `progreso`.

---

## Pendientes / TODO

- Cargar los `programa_url` faltantes en materias de los planes nuevos (todos menos industrial 2025, biomedica 2005, biomédica 2025 y TUSD 2025).
- Completar los `RTF` de `aeroespacial-2005`, porque se necesitan para calcular correctamente las condiciones de cursado de `Proyecto Integrador` y `Práctica Profesional Supervisada`.
- Completar los `RTF` de `ambiental-2025` (archivo `carreras/ambiental-2025.json`).
- Completar correlativas de Cs Biológicas.
---

## Cómo contribuir

- Reportá bugs o sugerencias mediante *Issues*.  
- Si querés agregar funcionalidades, hacé un *Fork*, realizá tus cambios y enviá un *Pull Request*.  
- ¡Toda ayuda es bienvenida!  

---

## Licencia

Este proyecto utiliza la licencia **MIT**, en línea con su inspiración, [FIUBA-Map](https://github.com/fdelmazo/FIUBA-Map).  

---

## Agradecimientos

- A **FdelMazo**, creador de **FIUBA-Map**, cuya estructura y diseño sirvieron como fuerte inspiración para esta versión adaptada a FCEFYN.  
- A la comunidad de estudiantes que aportan ideas y sugerencias para mejorar la herramienta.  

---
