# 🛡️ Active Directory: Guía de Instalación y Configuración Básica

Este tutorial te guiará paso a paso para crear y configurar un **Active Directory Domain Services (AD DS)** en un entorno de laboratorio utilizando **Windows Server 2019**. Ideal para estudiantes, administradores de red o entusiastas de la ciberseguridad.

## 📋 Requisitos
- 💻 Máquina virtual o física con:
  - [Windows Server 2019](https://archive.org/details/en_mftaah.com_windows_server_2019)
  - 2 GB RAM mínimo (recomendado 4 GB+)
  - 1 vCPU mínimo (recomendado 2+)
  - Disco de al menos 40 GB
- 🖥️ Acceso como administrador

---

## 🔧 Paso 1: Cambiar el nombre del equipo
1. Abrí el **Administrador del servidor**
2. Hacé clic en **Local Server**
3. En **Computer name**, hacé clic en el nombre
4. Cambiá el nombre a algo representativo (ej: `DC01`)
5. Reiniciá el equipo

---

## 🌐 Paso 2: Configurar IP estática
1. Abrí el **Panel de control > Centro de redes > Cambiar configuración del adaptador**
2. Clic derecho en el adaptador > Propiedades
3. Seleccioná **Protocolo de Internet versión 4 (TCP/IPv4)** > Propiedades
4. Ingresá una IP fija (ej: `192.168.1.10`), máscara, gateway y como DNS **usá la misma IP**

---

## 📦 Paso 3: Instalar el rol de Active Directory
1. En **Administrador del servidor** > clic en **Agregar roles y características**
2. Tipo de instalación: `Instalación basada en características o roles`
3. Seleccioná tu servidor
4. Roles: Activá **Active Directory Domain Services**
5. Características: dejá por defecto
6. Instalá y esperá a que finalice

---

## 🏗️ Paso 4: Promocionar el servidor a controlador de dominio
1. Una vez instalado el rol, hacé clic en el aviso amarillo > **Promover este servidor a controlador de dominio**
2. Elegí: `Agregar un nuevo bosque`
   - Nombre del dominio raíz: ej: `midominio.local`
3. Establecé una contraseña para el modo de restauración de servicios de directorio (DSRM)
4. Siguiente > dejar opciones por defecto
5. Esperá la validación y clic en **Instalar**
6. El servidor se reiniciará automáticamente

---

## ✅ Paso 5: Verificar la instalación
Después del reinicio:
- El servidor ya es un **Controlador de Dominio (DC)**
- Desde el **Administrador del servidor**, accedé a:
  - `Herramientas > Usuarios y equipos de Active Directory`
  - `Herramientas > DNS` para comprobar zonas directas e inversas

---

## 👤 Paso 6: Crear usuarios y unidades organizativas (OU)
1. Abrí **Usuarios y equipos de Active Directory**
2. Clic derecho en el dominio > `Nuevo > Unidad organizativa`
   - Ejemplo: `TI`, `Contabilidad`, `RecursosHumanos`
3. Dentro de cada OU, podés:
   - Clic derecho > `Nuevo > Usuario`
   - Crear grupos, aplicar políticas, etc.

---

## 🔒 Paso 7: Crear una política de grupo básica (GPO)
1. Abrí **Herramientas > Administración de directivas de grupo**
2. Clic derecho en el dominio u OU > `Crear un GPO`
   - Ejemplo: `PolíticaInicioSesión`
3. Editá el GPO:
   - Configuración de usuario > Plantillas administrativas > Sistema > `Ejecutar estos programas al iniciar sesión`

---

## 💡 Tips adicionales
- El sufijo `.local` no es obligatorio, pero es común en entornos internos.
- Podés unir máquinas al dominio desde otras VMs Windows usando las credenciales de administrador del dominio.
- Si usás VirtualBox o VMware, asegurate de estar en modo red "Host-only" o "Red Interna".

---

## 🧪 ¿Y después?
- 🧑‍💻 Crear scripts de inicio de sesión (logon scripts)
- ⚙️ Implementar políticas de seguridad (contraseñas, bloqueo, etc.)
- 🧑‍🏫 Usar este entorno para practicar ataques y defensas en Active Directory (Red Team / Blue Team)

---

## 📂 Recursos útiles
- [Documentación oficial de Microsoft](https://docs.microsoft.com/en-us/windows-server/)
- [Lista de comandos PowerShell para AD](https://docs.microsoft.com/en-us/powershell/module/addsadministration/)

---

## 🧑‍🏫 Autor

Explicación elaborada por [Sebastian Peinador](https://www.linkedin.com/in/sebastian-j-peinador/) para propósitos didácticos y de investigación en ciberseguridad ofensiva.

---

## 📄 Licencia

Este material se distribuye bajo la licencia [MIT](LICENSE).

---

> Si te resulta útil, ¡no olvides darle ⭐ al repo o compartirlo!
