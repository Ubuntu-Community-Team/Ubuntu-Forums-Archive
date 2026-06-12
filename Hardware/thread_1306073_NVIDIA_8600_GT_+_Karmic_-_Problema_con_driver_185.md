---
title: "NVIDIA 8600 GT + Karmic - Problema con driver 185"
date: 2009-10-30
forum: Hardware
---

### Post by fgl82 on 2009-10-30
Al upgradear a karmic como siempre me pasa con los upgrades de version, se me rompio el video.

corriendo dmesg pude ver que el problema parecia ser que el kernel tenia una version distinta de los drivers con respecto a los que se bajan del repositorio oficial.

Buceando por los foros encontre que esto lo resuelve:

sudo dpkg-reconfigure nvidia-185-kernel-source

Saludos!

---

### Post by VastOne on 2009-10-30
> **fgl82 said:**
> Al upgradear a karmic como siempre me pasa con los upgrades de version, se me rompio el video.

corriendo dmesg pude ver que el problema parecia ser que el kernel tenia una version distinta de los drivers con respecto a los que se bajan del repositorio oficial.

Buceando por los foros encontre que esto lo resuelve:

sudo dpkg-reconfigure nvidia-185-kernel-source

Saludos!

When karmic upgrade as always happens with version upgrades, I broke the video.

run dmesg I could see that the problem seemed to be that the kernel had a different version of the drivers with respect to which descend from the official repository.

Diving for the forums I found that this solves it:

sudo dpkg-reconfigure nvidia-185-kernel-source

Greetings

(I know Google translate is not the best. Feel free to correct my translation)

---

### Post by fgl82 on 2009-10-30
> **VastOne said:**
> When karmic upgrade as always happens with version upgrades, I broke the video.

run dmesg I could see that the problem seemed to be that the kernel had a different version of the drivers with respect to which descend from the official repository.

Diving for the forums I found that this solves it:

sudo dpkg-reconfigure nvidia-185-kernel-source

Greetings

(I know Google translate is not the best. Feel free to correct my translation)

As it always happens to me during version upgrades, when I upgraded to Karmic my video drivers stopped working.

I ran dmesg and saw that the problem seemed to be that the driver present in the kernel was not the one present in the repositories.

Searching through the forums I found a solution:

sudo dpkg-reconfigure nvidia-185-kernel-source

Greetings!

---

### Post by VastOne on 2009-10-30
> **fgl82 said:**
> As it always happens to me during version upgrades, when I upgraded to Karmic my video drivers stopped working.

I ran dmesg and saw that the problem seemed to be that the driver present in the kernel was not the one present in the repositories.

Searching through the forums I found a solution:

sudo dpkg-reconfigure nvidia-185-kernel-source

Greetings!

Gracias Senor

---

### Post by rubioo on 2009-10-30
flg82 a que te referis con "se me rompio el video.", porque yo tengo la misma placa de video y tengo algunos problemas.
Para saber si es el mismo problema que el tuyo y puedo solucionarlo :)

---

### Post by fgl82 on 2009-10-30
En realidad es una placa de video, no de red =P

El problema es que luego de las actualizaciones no me entra al entorno grafico.

En este caso el dmesg decia que la verison que habia bajado del repo era la 185.36 ponele y que el kernel tenia la 185.14 o algo asi.

corriendo el comando de ese, se soluciona este problema en particular.

Igual cualquier cosa preguntame porque pase varios problemas distintos ya  =P

---

### Post by rubioo on 2009-10-30
Como me voy a confundir asi ¬¬
 Mi problema es con compiz. Funciona, pero cuando quiero, por ejemplo, 'girar el cubo' dice que se cerro la aplicacion y me dice que lo reporte (con un boton que dice reportar), pero como no tengo internet :S

---

### Post by fgl82 on 2009-10-30
Ah flor de problema =P

ni idea, es re generico el error, probaste instalar una version anterior de los drivers? la 173 quiza?

---

### Post by rubioo on 2009-10-30
No probe esos drivers. Ahora estoy usando la version 185.
El problema que tengo que es que se 'cierra' compiz cuando quiero cambiar de escritorio.

---

### Post by guillermolisi on 2009-10-30
> **VastOne said:**
>  Feel free to correct my translation)
Ponete comoda y escribi en Español ya que estas en el foro del Argentina LoCo Team.

---

### Post by rubioo on 2009-10-30
Si ejecuto compiz luego de iniciar mi sesion, me sale esto:

> 
cristian@cristian-desktop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: 
Segmentation fault (core dumped)


---

### Post by fgl82 on 2009-10-30
Si, por eso, mi recomendación es que pruebes los drivers anteriores a ver si el problema es con los drivers más nuevos

---

### Post by rubioo on 2009-10-30
Si, ya me fije con los drivers anteriores pero nada sigue igual :S

---

### Post by fgl82 on 2009-10-30
lo unico que veo es lo de xgl not present que se solucionaria con 

sudo apt-get install xserver-xgl

Pero no se si servira para algo en tu caso o no, pero con probar...

AH! IMPORTANTE: FIJATE QUE TE DICE QUE ON PUEDE CARGAR LAS SLIDES APARENTEMENTE DEL CUBO ASI QUE FIJATE DESHABILITANDO LAS IMAGENES DE ARRIBA Y ABAJO DEL CUBO O CUALQUIR COSA QUE TENGAS QUE ESTE TRATANDO DE USAR ESE PNG INEXISTENTE.

---

### Post by rubioo on 2009-10-30
Creando otro usuario funciona como siempre compiz (sin problemas).
Pero como tengo problemas con internet, voy a aprovechar y a instalar desde cero, y ademas aprovecho para poner mi home aparte.
Igual fgl82 gracias por la buena onda :)

---

