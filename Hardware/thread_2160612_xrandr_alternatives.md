---
title: "xrandr alternatives?"
date: 2013-07-07
forum: Hardware
---

### Post by Marcelo Ramone on 2013-07-07
Hi,

I'm trying to resize the LCD monitor (secondary HDMI monitor) because Ubuntu does not recognize the screen properly and the desktop borders are outside the screen.

Are there alternatives to xrandr utility?

xrandr is not available for Ubuntu 13.04

Thanks.-

---

### Post by jp734 on 2013-07-07
xrandr should be available on Ubuntu 13.04 coz I have Lubuntu 13.04 (LXDE) and it works but not after I turned Xinerama on. Xinerama and xrandr don't work well together. It's either one or the other. This might be your case.

I am not that familiar with the xrandr commands yet so I stick with Xinerama and xorg.conf file for now. I have to start learning it well though as one day, xorg.conf will not be used totally (I guess). Linux Mint forums are already saying xorg.conf is not needed anymore and is not recommended.

---

### Post by Ranko Kohime on 2013-07-07
Yeah, running xrandr here as well.

There's also a GUI front-end to it, arandr, which allows you to move the displays around, activate/deactivate and resize, and saving the layout generates a shell script with the xrandr command in it.  :)

---

### Post by papibe on 2013-07-07
> **Marcelo Ramone said:**
> ...the desktop borders are outside the screen.

Hi Marcelo Ramone.

Is this an LCD monitor or an HDTV?

Regards.

---

### Post by Marcelo Ramone on 2013-07-07
Hello,

My mistake, is a HDTV generic.
I'll try [COLOR=#000000]arandr later, i hope it's in the repositories, because [/COLOR][COLOR=#000000]xrandr is not instalable in my 13.04 installation.[/COLOR]

---

### Post by papibe on 2013-07-07
Thanks.

Then most likely it is an [Overscan]("http://en.wikipedia.org/wiki/Overscan") problem. In other words, a problem in the HDTV settings.

Most current TV's have the ability to set how the signal is reproduced. In case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area. In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

Play with the options available on your TV, may be the option is not easy to see. Check your manual or research about it on the Internet.

Let us know how it goes,
Regards.

---

### Post by Marcelo Ramone on 2013-07-07
hello

i tryied display settings before but this model has not the options you described.

with ati official driver this problem was fixed but the driver broke unity and other problems..

open source driver is better.

thank you.

---

### Post by Marcelo Ramone on 2013-07-07
```
marcelo@pc02:~$ sudo apt-get install xrandr randrLeyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
El paquete xrandr no está disponible, pero algún otro paquete hace referencia
a él. Esto puede significar que el paquete falta, está obsoleto o sólo se
encuentra disponible desde alguna otra fuente
Sin embargo, los siguientes paquetes lo reemplazan:
  x11-xserver-utils:i386 x11-xserver-utils


E: El paquete «xrandr» no tiene un candidato para la instalación
E: No se ha podido localizar el paquete randr



```

---

### Post by papibe on 2013-07-08
> **Marcelo Ramone said:**
> ...this model has not the options you described.
Sorry to hear that.

BTW, xrandr is part of the x11-xserver-utils package, which comes preinstalled. 

Regards.

---

