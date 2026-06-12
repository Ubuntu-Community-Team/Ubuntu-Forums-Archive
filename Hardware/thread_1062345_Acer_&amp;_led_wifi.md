---
title: "Acer &amp; led wifi"
date: 2009-02-06
forum: Hardware
---

### Post by Mauro22 on 2009-02-06
Buenas!


Otra vez molestando por aca.


Mi modelo de Acer Aspire (5730-4700) no enciende el led wifi, ni fijo ni intermitente ni nada.

Probe al que habian posteado ("dev led.softpin...") y no funciono.

Probe algo de iw2200 o algo asi y tampoco.

Luego lei que usando los drivers de madwifi puede ser que funcione. Pero necesito mas info para no meter la pata.

esta es la placa (segun lspci):

```

03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

Y en la etiqueta dice que esta pegada en la notebook dice:

```

Acer Nplify 802.11b/g Draft-N WLAN

```


Gracias por vuestro tiempo!:p

---

### Post by luks911 on 2009-02-07
No encontré mucho sobre esa placa y no estoy seguro de que esté soportada por madwifi. No obstante, si considerás que vale la pena, la prueba debería ser indolora. ¿Ahora qué driver usás, ath9k?
Deberías poner el módulo que usa ahora en blacklist. Bajar y compilar la última versión de madwifi de acá[0]. 
Acá[1] hay un tutorial para hacerlo que podés usar de base. Salteate los pasos para poner en blacklits el driver madwifi que instala por defecto ubuntu, que no deberías tener si usás ath9k y es una versión distimta al que vas a compilar.
Si lo completas sin errores y no funciona, lo desinstalás yendo a la carpeta que se generó al descomprimir el driver y ejecutás
```
sudo make uninstall
```
y sacás del blacklist el ath9k. Así queda todo como antes.
Cualquier duda o error, preguntá. Sé que no fui demasiado explícito :-P

[0] [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)
[1] [http://ubuntu-ar.org/tutoriales/ar5007eg](http://ubuntu-ar.org/tutoriales/ar5007eg)

---

### Post by moonport on 2009-02-25
Yo tengo la siguiente placa en mi Compaq:
Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

y solucioné el tema del driver con el de madwifi ([http://www.madwifi.org/](http://www.madwifi.org/)).

El led sigue sin funcionar y es un bug reportado en el kernel de Linux como pendiente de arreglo.

Slds.

---

### Post by luks911 on 2009-02-25
> **moonport said:**
> Yo tengo la siguiente placa en mi Compaq:
Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

y solucioné el tema del driver con el de madwifi ([http://www.madwifi.org/](http://www.madwifi.org/)).

El led sigue sin funcionar y es un bug reportado en el kernel de Linux como pendiente de arreglo.

Slds.

El led lo podés hacer funcionar con esto ([http://ubuntuforums.org/showthread.php?t=983511](http://ubuntuforums.org/showthread.php?t=983511)).

Saludos

---

### Post by moonport on 2009-03-05
Voy a probarlo.
Muchas Gracias.
Slds.

---

### Post by moonport on 2009-03-11
Funcionó perfectamente.
Gracias luks911.
Slds.

---

