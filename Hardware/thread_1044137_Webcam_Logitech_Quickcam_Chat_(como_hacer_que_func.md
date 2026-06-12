---
title: "Webcam Logitech Quickcam Chat (como hacer que funcione en 8.10)"
date: 2009-01-19
forum: Hardware
---

### Post by atari130xe on 2009-01-19
Gente le instalé Ubuntu 8.10 en su PC a un amigo le regalaron una webcam y es una Logitech Quickcam Chat la de foto adjunta.
Instalé Cheeze y funciona bién la toma y la imagen es buena.
Eh aqui que no funciona en aMSN ni en Kopete, directamente tiene una imagen en negro (como si no la detectara) y obviamente no aparecen los típicos controles de brillo, etc.

aca va lo que "tira" el sistema:

```
emiliano@emiliano-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:092c Logitech, Inc. QuickCam Chat
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
emiliano@emiliano-desktop:~$ 

```

```
emiliano@emiliano-desktop:~$ lsmod |grep spca
gspca_spca561          19328  0 
gspca_main             29312  1 gspca_spca561
videodev               41344  1 gspca_main
usbcore               149360  5 gspca_spca561,gspca_main,uhci_hcd,ehci_hcd
emiliano@emiliano-desktop:~$
```

alguna idea de como solucionarlo? lo que vi en Google es un poco viejo y antes de hacer lio prefiero consultar a ver si alguien la tiene y funcionando.
gracias!

Nada? no comprendo porque por ejemplo funciona perfectamente en Cheese y no con aMSN o con Kopete, alguien podria tirarme una soga? (no pa colgarme por favor :p)

---

### Post by atari130xe on 2009-01-29
Bump.... nadie me puede tirar una idea de que pude ser?
saludos!:D

---

### Post by atari130xe on 2009-01-29
> **atari130xe said:**
> Bump.... nadie me puede tirar una idea de que pude ser?
saludos!:D

PD: por lo poco que entiendo hay un problema de direccionamiento de puerto de video, /dev/video0 a /dev/video1, alguien podria indicarme como redireccionarlo? googleé pero no encontré nada. gracias

---

### Post by agarzon on 2009-03-01
Creo que el problema es de compatibilidad de librerias. Tengo el mismo problema en dos maquinas diferentes, las dos con Ubuntu 8.10 de 64 bits.

Una tercera maquina (la de mis padres) tiene el mismo problema. La camara funcionaba con Ubuntu 7.10 y al actualizar a 8.10 se revento.

Creo que deberias intentar haciendo el post en ingles. Quizas tengas mas suerte.

---

