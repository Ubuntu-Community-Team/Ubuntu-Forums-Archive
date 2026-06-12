---
title: "Problema al Upgrading to Karmic"
date: 2009-10-30
forum: Instalación y Actualización
---

### Post by RafaelG on 2009-10-30
Hola Bueno he realizado el Upgrade deacuerdo a las indicaciones de Ubuntu. La actualizacion que utilize fue desde Update Manager todo marchaba OK hasta el momento donde la pantalla se va a Blackout y muestra el siguiente mensaje 
 
**Problema de instalacion**
**La configuracion de Gnome No se ha instalado correctamente por favor contactarse con el administrador del computador.**
 
De hay en adelante solo me queda apagar el Notebook ( Dell Vostro 1510) desde el Boton ya que se queda pegado en esa patalla negra.
 
_**Nota:**_ No he podido descargar el Cd ya que ninguna localidad me ha funcionado correctamente.

---

### Post by moreback on 2009-10-30
> **RafaelG said:**
> _**Nota:**_ No he podido descargar el Cd ya que ninguna localidad me ha funcionado correctamente.

Bájalo por bittorrent.

[http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent)

[http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent)

---

### Post by Carlos C on 2009-10-30
> **RafaelG said:**
> No he podido descargar el Cd ya que ninguna localidad me ha funcionado correctamente.

¿Miraste [acá]("http://ubuntuforums.org/showthread.php?t=1250302")?

Saludos.

---

### Post by RafaelG on 2009-11-01
Hola Carlos & MoreBack gracias por la direccion ya tengo el CD, he estado googliando buscando una Solucion a mi Problema pero hasta el momento no he encontrado nada, por otro lado he tratado de montar la particion que utilizo desde el LiveCD para recuperar mi Home y files sin tener resultado obteniendo el siguiente error: 

**Error mounting: mount exited with exit code32:mount: wrong fs type, bad option, bad superblock on/dev/sda7, missing cadepage or helper program, or other error  in some case useful into is found in syslog  - try dmesg  tail or so.**

Agradeciendo ante mano cualquier ayuda a mi problema.

---

### Post by Carlos C on 2009-11-02
Dinos cuál comando estás usando para montar la partición, eso es importante.
Saludos.

---

### Post by RafaelG on 2009-11-02
> **Carlos C said:**
> Dinos cuál comando estás usando para montar la partición, eso es importante.
Saludos.


Hola Carlos el codigo utilizado fue: **sudo fsck -cf /dev/sda7**

---

### Post by RafaelG on 2009-11-02
Hola bueno Hize lo siguiente para reparar los paquetes y poder ingresar a ubuntu por el momento

**Modo Recovery>Reparar Paquetes**
Finalizo la reparacion y entre sin ningun problema.

Ahora mi problema sigueciendo el Upgrade  para karmic ya que al momento de ir a Update manager me aparece el siguiente error:

[http://img267.imageshack.us/img267/4771/screenshotvp.png]("http://img267.imageshack.us/img267/4771/screenshotvp.png")

---

### Post by moreback on 2009-11-02
Cámbiate al Servidor Oficial, el mirror chileno está incompleto.

---

### Post by RafaelG on 2009-11-03
> **moreback said:**
> Cámbiate al Servidor Oficial, el mirror chileno está incompleto.

ahora si lo cambie a main sever y todo bien ahora si pero ahora tengo otro problema que es con la Broadcom wireless abri otro thread.

Gracias por los Post y las ayudas ahora seguire en mi otro Thread buscando hace Funcionar mi Wireless Broadcom

---

