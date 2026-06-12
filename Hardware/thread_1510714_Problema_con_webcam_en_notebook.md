---
title: "Problema con webcam en notebook"
date: 2010-06-15
forum: Hardware
---

### Post by santiago79 on 2010-06-15
Hola gente como andan?
miren tengo un problema me compre una notebook asus K52J com una webcam integrada
el problema es que funciona invertida osea de cabeza ya probe muchas cosas para poder invertirla hasta con cheese y no puedo
no tengo vflip y ya probe con la libreria v4l2ucp pero no me da la opcion de rotar

USB2.0 UVC VGA WebCam eso me sale en el modelo

si alguien sabe como modificarla para que funcione bine
tengo ubuntu 10 instalado
muchas gracias

---

### Post by luks911 on 2010-06-17
Encontré esto[0] y puede que te sirva. Básicamente se trata de instalar una versión modificada de una de las librerías que maneja la cámara.
Los pasos son, en una terminal:

```
sudo add-apt-repository ppa:libv4l/ppa
sudo apt-get update
sudo apt-get install libv4l-0
```

Después, aunque tal vez no sea necesario y deberías probarlo, las aplicaciones que usan la cámara deberías ejecutarlas desde una terminal de este modo

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so aplicación
```

Por ejemplo, en el caso de Cheese

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
```

[0] [http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/](http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/)

---

### Post by santiago79 on 2010-06-17
mira no pude solucionarlo con eso instale comorama que lei que podia configurarla, pero me tira un error al iniciar

santiago-ubuntu@santiago-ubuntu:~$ lsusb
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5094 IMC Networks 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


el error es este

Could not conenect to video device (/dev/video0).
please check connection

el amsn emesene o chese me la detectan pero estoy de cabeza.

---

