---
title: "Problema actualización a karmic (Failed to fetch)"
date: 2009-10-31
forum: Instalación y Actualización
---

### Post by VonlisT on 2009-10-31
Bueno, intentando actualizar a karmic koala desde jaunty jackalope, me percaté que cuando faltaban 3 paquetes de los 1226 que debía descargar me lazó un error con un mensaje como este:
"Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/python-ubuntuone-client_1.0.2-0ubuntu2_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/python-ubuntuone-client_1.0.2-0ubuntu2_all.deb) 404 Not Found"
La solución fue bastante simple, se me ocurrió descargar los paquetes manualmente desde:
[https://launchpad.net/ubuntu/+source/ubuntuone-client/1.0.2-0ubuntu2/+build/1313042](https://launchpad.net/ubuntu/+source/ubuntuone-client/1.0.2-0ubuntu2/+build/1313042)

Una vez descargados, entré como root en nautilis (desde consola: sudo nautilus), y fui hasta /var/cache/apt/archives y los pegué allí, volví a ejecutar la actualización completa del sistema y ahora se saltó a la instalación ya que reconoció que se había descargado los 3 paquetes faltantes (los 3 que me faltaban están en el mismo link de más arriba)

Saludos :D

---

### Post by moreback on 2009-10-31
parece que esas actualizaciones de Ubuntu One no han sido transferidas al mirror chileno, si te cambias al oficial no hay problemas.

---

### Post by aribet on 2009-11-01
Yo tengo el mismo problema pero no logro dar con los archivos para 64 bits,
entonces cómo hago el cambio del mirror chileno al oficial.

Gracias

---

### Post by VonlisT on 2009-11-01
> **aribet said:**
> Yo tengo el mismo problema pero no logro dar con los archivos para 64 bits,
entonces cómo hago el cambio del mirror chileno al oficial.

Gracias

Me imagino que debes editar el archivo /etc/apt/sources.list y cambiar el prefijo cl por el del repositorio oficial, así cambiarás la ruta de descarga. Deberçia quedar algo así:
>  deb [http://**us](http://**us)**.archive.ubuntu.com/ubuntu/ jaunty main
luego sólo actualizas la lista con: sudo apt-get update
entonces ahora actualizas la distro completa.

De todos modos, encontré un archivo para tu arquitectura:
[https://launchpad.net/ubuntu/+source/ubuntuone-client/1.0.2-0ubuntu1/+build/1299634](https://launchpad.net/ubuntu/+source/ubuntuone-client/1.0.2-0ubuntu1/+build/1299634)

Si buscas en esa misma página, seguramente encontrarás los paquetes restantes que necesitas.

Saludos

---

### Post by moreback on 2009-11-01
Más fácil:

**Sistema -> Administración -> Orígenes del software**, pestaña Software de Ubuntu, seleccionar "**Servidor principal**" en "Descargar desde:"

Saludos.

---

