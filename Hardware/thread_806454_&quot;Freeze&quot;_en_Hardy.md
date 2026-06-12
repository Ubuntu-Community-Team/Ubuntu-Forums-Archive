---
title: "&quot;Freeze&quot; en Hardy"
date: 2008-05-25
forum: Hardware
---

### Post by Mauro22 on 2008-05-25
Buenas!!


Tengo un problemilla.


Cada tanto ubuntu se freeza tanto el entorno grafico como el teclado, no asi el mouse.

Esto dura unos 7 segundos y lo hace cada, digamos, 10 minutos mas o menos. ( a veces varias veces en el mismo minuto :S )


Esto se hace cada vez con mas frecuencia mientras mas este encendida la PC (asi que debe ser algo de calor o algo asi)

Hay alguna forma de averiguar que es? o si a alguien mas le pasa?


La placa de video es un 6100 onboard
Motherboard: Gigabyte con chipset nvidia



Gracias desde ya!

---

### Post by osensei on 2008-05-25
Estás usando alguna placa wifi? yo tengo un problema similar con los drivers de mi placa wifi: después de un largo tiempo, que suelen ser vaaaaarias horas (en general lo suelo notar al día siguiente después de haber quedado la notebook prendida toda la noche), empieza a trabarse y destrabarse cíclicamente, detecté que el problema era con los drivers de mi placa wifi, que estoy usando un snapshot de madwifi especial para mi chipset (AR5007EG). Así que como en general la uso por puerto ethernet, deshabilité la carga automática del módulo, y sólo lo cargo cuando lo necesito.

La próxima vez que te pase escribí en la consola el comando "dmesg" que te va a mostrar los mensajes del kernel, ahí podés llegar a identificar el problema. Si querés podés poner 
```
dmesg | tail
```
Que te va a mostrar los últimos 10 mensajes. Postealos después acá a ver si te podemos dar una mano con eso.

Saludos!

---

### Post by Mauro22 on 2008-05-25
Si, Wifi tengo, 

La compre justo cuando salio HH porque en gusty no la tomaba. Hardy la reconocio de una asi que no se que drivers usa.


No tengo notebook asi que no puedo apagarla y prenderla, aparte lo uso todo el dia. 

Me quedo tranquilo porque el hardware no es porque en windows no pasa nada raro.


Esta es la salida del comando (sin que pase nada)

 ```

[   64.171621] wlan0: Initial auth_alg=0
[   64.171636] wlan0: authenticate with AP 00:1b:11:d6:5e:eb
[   64.172892] wlan0: RX authentication from 00:1b:11:d6:5e:eb (alg=0 transaction=2 status=0)
[   64.172898] wlan0: authenticated
[   64.172900] wlan0: associate with AP 00:1b:11:d6:5e:eb
[   64.176769] wlan0: RX AssocResp from 00:1b:11:d6:5e:eb (capab=0x421 status=0 aid=1)
[   64.176774] wlan0: associated
[   64.176778] wlan0: switched to short barker preamble (BSSID=00:1b:11:d6:5e:eb)
[   64.177834] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   78.773913] wlan0: no IPv6 routers present

```

---

