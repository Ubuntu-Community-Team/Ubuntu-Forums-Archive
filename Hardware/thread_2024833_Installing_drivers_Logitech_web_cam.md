---
title: "Installing drivers Logitech web cam"
date: 2012-07-14
forum: Hardware
---

### Post by alkaza on 2012-07-14
Hi, I discovered a old webcam in a drawer, It's a Logitech QuickCam Express:
> Bus 005 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express
Searching information about drivers I found this:
[https://help.ubuntu.com/community/Spca5xx](https://help.ubuntu.com/community/Spca5xx)

I've followed the steps but, when I've tried to install this:
```
 sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
```
It has appear this:
```
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete linux-restricted-modules-3.2.0-23-generic
E: No se pudo encontrar ningún paquete con la expresión regular «linux-restricted-modules-3.2.0-23-generic»
E: No se ha podido localizar el paquete gcc-3.4
E: No se pudo encontrar ningún paquete con la expresión regular «gcc-3.4»

```

I've looking for linux-headers 3.2.0-23 in synaptic but only appears 3.2.0-24 to 26.
What's wrong? Do I need upgrade my kernel?

Thanks

---

### Post by alkaza on 2012-07-16
Can anybody help me?

---

