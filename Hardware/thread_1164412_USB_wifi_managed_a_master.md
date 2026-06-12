---
title: "USB wifi managed a master"
date: 2009-05-19
forum: Hardware
---

### Post by Transgenic on 2009-05-19
Inauguro el nuevo foro dandole mis felicidades por el espacio adquirido en Ubuntu Forums
):P

Mi problema estaba planteado en el foro anterior
[http://foros.ubuntu-cl.org/viewtopic.php?t=8294](http://foros.ubuntu-cl.org/viewtopic.php?t=8294)

He descubierto algunas cosas, y ahora no sigue la misma linea.

Es un USB Wifi D-Link, desde un principio funciono (no lo sabia) y lo hace como Managed. Necesito configurarlo para que este en modo master pero al intentar hacer esto no funciona.
El comando que encontre para hacerlo es **iwconfig *wlan1* mode master**


**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:-2147483648 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```




Gracias de antemano :p

---

### Post by Carlos C on 2009-05-19
¿y qué ocurre cuando ejecutas ese comando?, ¿obtienes algún tipo de error?

---

### Post by Transgenic on 2009-05-19
Sabia que algo se me olvidaba.
Esto es lo que me aparece:

```
$ iwconfig wlan1 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan1 ; Operation not permitted.
```


y si lo hago como root (creo que asi se dice, lo que hice fue introducir el comando **su** y la pass) resulta esto:

```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan1 ; Invalid argument.

```

---

### Post by Carlos C on 2009-05-20
Creo que hay un punto importante a tener en cuenta. No estoy tan seguro que puedas dejarlo en modo "master". En el man de iwconfig dice:
 > Master(the node is the synchronisation master or acts as an Access Point)Tu lo quieres usar para acceder a la red, ¿verdad?, es decir, como usarías una tarjeta wifi normal, ¿no es así?

---

### Post by 3nG3ndR0 on 2009-05-20
sorry como soy novato alguien me podría decir cual son las diferencias, en que este en managed y master porque me di cuenta que mi wireless dice managed igual.

---

### Post by Transgenic on 2009-05-20
@[[COLOR=#339900]**Carlos C**[/COLOR]]("http://ubuntuforums.org/member.php?u=469233"): No. Yo quiero dejarlo en modo master para acceder con mi Nintendo DS al wifi. He ahi el problema, porque para buscar señales y conectarme a travez de ellas desde mi PC no tengo ningun problema, pero no es mi proposito.

@[3nG3ndR0]("http://ubuntuforums.org/member.php?u=838115"): El modo managed es para escanear conexiones a tu alcance, y master es para generar un punto de acceso o generar wifi.

---

### Post by Transgenic on 2009-05-30
Hasta que di con una solucion. En realidad no es solucion, sino una respuesta a que no se puede hacer hasta el momento.

En esta pagina se muestra lo que puede hacer y lo que no.
[http://linuxwireless.org/en/users/Drivers/zd1211rw](http://linuxwireless.org/en/users/Drivers/zd1211rw)

Gracias de todos modos.

Saludos :D

---

