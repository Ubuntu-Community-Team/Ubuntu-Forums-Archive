---
title: "poner Ralink RT2860 en modo monitor"
date: 2009-08-17
forum: Hardware
---

### Post by ClarkXP on 2009-08-17
Hola.

Les cuento que me compre un notebook Acer Aspire 4535
Era tan feliz... instalé ubuntu 9.04 sin problemas, (me reconocio wifi altiro, la red tuve que levantar un modulo... pero son detalles).

La cuestion es que como funciono altiro no me fije en la marca.
Cuando estaba instalando las cosas necesarias para monitoriar redes... de pronto se me calló la cara:

Ralink RT2860.. yo pense de primera que era atheros.

He buscado info por todos lados, pero no logro encontrar mucha info acerca de esta tarjeta.

Si alguien tiene alguna exp con esta si me puede ayudar.

Lo unico que encontre es que si existe un driver, pero solo funciona modo monitor, pero no para inyeccion de paquetes en paralelo.

Saludos!

---

### Post by CdK1 on 2009-08-17
Puedes instalar desde los repositorios;

rt2860-source - source for RT2860 wireless adapter kernel module     ò

entras a [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) y te bajas el driver, al desempaquetarlo encontrarás:

 Caturra:/home/CdK1# cd /usr/local/src/
Caturra:/usr/local/src# wget [http://www.ralinktech.com.tw/data/drivers/2009_0521_RT2860_Linux_STA_V2.1.2.0.tgz](http://www.ralinktech.com.tw/data/drivers/2009_0521_RT2860_Linux_STA_V2.1.2.0.tgz)
--2009-08-17 10:40:31--  [http://www.ralinktech.com.tw/data/drivers/2009_0521_RT2860_Linux_STA_V2.1.2.0.tgz](http://www.ralinktech.com.tw/data/drivers/2009_0521_RT2860_Linux_STA_V2.1.2.0.tgz)
Resolviendo [www.ralinktech.com.tw](www.ralinktech.com.tw)... 192.72.83.242
Connecting to [www.ralinktech.com.tw|192.72.83.242|:80](www.ralinktech.com.tw|192.72.83.242|:80)... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 643879 (629K) [application/x-compressed]
Saving to: `2009_0521_RT2860_Linux_STA_V2.1.2.0.tgz'

100%[================================================================================================================>] 643.879     73,3K/s   in 9,5s    

2009-08-17 10:40:42 (66,5 KB/s) - `2009_0521_RT2860_Linux_STA_V2.1.2.0.tgz' saved [643879/643879]

Caturra:/usr/local/src# tar vxzf 2009_0521_RT2860_Linux_STA_V2.1.2.0.tgz

Caturra:/usr/local/src# cd 2009_0521_RT2860_Linux_STA_V2.1.2.0 
Caturra:/usr/local/src/2009_0521_RT2860_Linux_STA_V2.1.2.0# less README_STA 

Y sigues los pasos de esta página:

[http://ubuntuforums.org/showthread.php?t=683085&page=4](http://ubuntuforums.org/showthread.php?t=683085&page=4)

---

### Post by ClarkXP on 2009-08-17
Si este driver lo baje... este mismo se usa para poner en modo monitor??
yo lo use para activar el soporte a wpa/wpa2, habia que modificar un archivo de configuracion y luego compilar e instalar el modulo.

con respecto al tread que linkeaste solo sale para instalar ralink en versiones antiguas de ubuntu donde no venía el driver.

Saludos.

---

### Post by Carlos C on 2009-08-19
Acá puedes encontrar algo de información. No es la solución exacta a tu problema pero creo que no está demás que lo revises:

[http://ubuntuforums.org/showthread.php?t=966185&highlight=ralink+rt2860](http://ubuntuforums.org/showthread.php?t=966185&highlight=ralink+rt2860)

Saludos.

---

### Post by ClarkXP on 2009-09-01
weno, finalmente encontré una solucion...
es rutils
es un programa de gestion de coenxiones, (reemplazo de network manager, solo wifi)
permite bajar  y subir la interfaz de manera simple como monitor, manager y otros.
Luego airodump y todo bien :)

Leyendo muchas hojas descubri que las placas ralink no permiten inyeccion en paralelo...

Ya quiero que se agote la garantia para ponerle una atheros!! xD

---

### Post by ClarkXP on 2009-09-05
Ahora vengo a poner la solución completa.
Esto es la solución a dos problemas que trae el driver por defecto:

- Soporte para WPA/WPA2.

- Modo monitor.

Para lo primero, vamos al sitio oficial de Ralink
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

Descargamos las fuentes.
[LEFT][COLOR=Black]RT2860PCI/mPCI/PCIe/CB(RT2760/RT2790/RT2860/RT2890)[/COLOR]
[COLOR=Black]RT2860WebUI

Tenemos que instalar los headers del kernel y las herramientas basicas de compilacion.
[/COLOR]```
$ sudo aptitude install build linux-kernel-headers build-essential 
```[COLOR=Black]
Las descomprimimos en nuestro home y quedara una carpeta con los files dentro.
[/COLOR]```
$ cd ~/[carpeta del driver]/os/linux && gedit config.mk 
```buscamos las siguientes lineas y las dejamos tal cual aparece en el siguiente cuadro (y = yes, n = no)
> #ifdef WPA_SUPPLICANT_SUPPORT
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y
#endif // WPA_SUPPLICANT_SUPPORT //

#ifdef NATIVE_WPA_SUPPLICANT_SUPPORT
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
#endif // NATIVE_WPA_SUPPLICANT_SUPPORT //luego a compilar nuestro driver, primero volvemos a la carpeta principal donde estan las fuentes y compilamos.

```
$ sudo make

```luego instalamos:

```
sudo make install
```luego agregamos el modulo:

```
sudo modprobe rt2860sta
```si no tenemos problemas Bingo! ya tienes soporte para wpa/wpa2.
[/LEFT]
 ____
Ahora para poner esta placa en modo monitor
instalamos el siguiente paquete:
```
$ sudo aptitude install rutilt
```esta es una interfaz grafica muy simple de usar.
para usar el modo monitor, primero hay que bajar el wifi desde network manager, un simple click derecho sobre el icono de nm-applet y le sacas el ticket a activar inalámbrica.

abres el programa, creas un nuevo perfil como monitor y solo levantará la placa cuando apliques el perfil. para volver a network manager, vas a la ultima pestaña y haces click sobre el boton up (tiene que quedar en down), vuelves al icono de nm-applet y les pones el ticket y sigues normalmente.

Saludos.

---

