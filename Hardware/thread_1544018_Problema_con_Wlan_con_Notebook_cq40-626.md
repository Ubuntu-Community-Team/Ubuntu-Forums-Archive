---
title: "Problema con Wlan con Notebook cq40-626"
date: 2010-08-01
forum: Hardware
---

### Post by Simontero on 2010-08-01
El problema es que no me toma la wireless del notebook pero cuando coloco el Wireless USB funciona correctamente, coloque el comando:

lspci |grep Network

    y sale: 

09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

    Luego coloque el comando como sale en una pagina:

sudo aptitude install bcmwl-kernel-source

y no podia intalarlo al principio y tube que meterme a la pagina de ubuntu y descargar unos programas pequeños que pedían, me baje todos, pero al final pude intalarlo, el problema es que todavia no toma la WLAN del notebook, si pudieran ayudarme se agradeceria mucho.

---

### Post by Simontero on 2010-08-01
otro problema que tengo es que me meto a sistema > administración > controladores de hardware y me sale descargando y actualizando indice de paquetes, se demora un poco y se cierra, no tengo idea el por qué.

---

### Post by Carlos C on 2010-08-03
> **Simontero said:**
> otro problema que tengo es que me meto a sistema > administración > controladores de hardware y me sale descargando y actualizando indice de paquetes, se demora un poco y se cierra, no tengo idea el por qué.

Hola. Lo que puede estar pasando es que los repos de Chile estén caídos y por eso no puedes descargar los drivers. Prueba entrando en Sistema>Administración>Orígenes del software. En la pestaña "Software de Ubuntu" cambia tu opción de descarga, seguramente ahora tienes seleccionado "Servidorpara Chile", cámbialo a "Servidor principal" e intenta nuevamente.

También puedes mirar aquí:
[http://ubuntuforums.org/showthread.php?t=1539214](http://ubuntuforums.org/showthread.php?t=1539214)

espero que te sirva, no tengo claro qué versión de Ubuntu estás usando.
Saludos.

---

### Post by Simontero on 2010-08-10
Gracias, solucionado.

---

