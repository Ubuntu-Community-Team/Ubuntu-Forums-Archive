---
title: "micro AMD APU"
date: 2012-06-20
forum: Hardware
---

### Post by dirty fingers on 2012-06-20
Si compro uno de los nuevos micros de AMD que integran CPU y GPU (conocidos como APU) voy a poder usar XVBA ?

---

### Post by dirty fingers on 2012-08-05
Me respondo solo ahora que ya logre que funcionara.

La cuestión es así :

-Los modelos de ATI de la serie HD 4xxx en adelante utilizan para acelerar video HD lo que llaman VAAPI (desarrollado por intel al parecer)
[http://en.wikipedia.org/wiki/Video_Acceleration_API](http://en.wikipedia.org/wiki/Video_Acceleration_API)

-Los AMD APU vienen con Ati HD 6xxx en adelante.
[http://www.amd.com/us/products/desktop/apu/mainstream/Pages/mainstream.aspx#7](http://www.amd.com/us/products/desktop/apu/mainstream/Pages/mainstream.aspx#7)

-Para utilizar esto necesitamos 2 cosas: Los driver ATI que se pueden instalar fácilmente con el gtk-jockey , y un reproductor compilado con estas características. Por ahora el único que me funciono es el mplayer descargado de este ppa (que se puede usar con GUI smplayer por ejemplo)[ https://launchpad.net/~sander-vangrieken/+archive/vaapi]("https://launchpad.net/%7Esander-vangrieken/+archive/vaapi")
Se puede compilar también desde [https://gitorious.org/vaapi/mplayer](https://gitorious.org/vaapi/mplayer)

-En 1920x1080 el uso de cpu es de 7% promedio.

---

### Post by dirty fingers on 2012-08-22
Un pequeño detalle que no mencione... hay que tener el paquete "xvba-va-driver" instalado y se puede verificar si todo esta bien usando en la terminal "vainfo" que debería devolver algo como:
> libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD


---

