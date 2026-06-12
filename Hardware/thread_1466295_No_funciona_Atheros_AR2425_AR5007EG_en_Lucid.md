---
title: "No funciona Atheros AR2425 AR5007EG en Lucid"
date: 2010-04-30
forum: Hardware
---

### Post by jecho3k on 2010-04-30
Hola les cuento que tengo un MSI Wind U100 que siempre me había dado problemas con la tarjeta Wi-Fi. Si bien el internet a ratos funcionaba, en algunos momentos se caia la señal, etc. Decidí cambiar la tarjeta wireless por una con chipset Atheros, que me habían recomendado pues tenían drivers libres.

Es así como me compré una Tarjeta WiFi Mini PCI Express Atheros AR2425 AR5007EG AR5BXB63 802.11b/g.

La probé con el S.O. Eeebuntu (basado en Ubuntu 9.04) y si bien la reconoció, no encontró ninguna red inalámbrica cercana. Le puse un

```
lspci | grep Wireless
```

y me apareció: ```
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

Como coincidió con que tenía un kernel antiguo que no incluía el driver ath5k, encontré normal que no me funcionara. Así que decidí actualizar a Ubuntu 10.04 Lucid Lynx, pensando en que funcionaría sin problemas.

Al instalar Ubuntu 10.04, me encuentro con que si bien la tarjeta encuentra las redes, me fue imposible conectarme a la mia (encriptada con WPA2 AES) y menos a las otras. Le hago un lspci | grep Wireless  nuevamente, pero ahora me aparece:

```
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

El modelo cambió (con el chipset al parecer) :s y me sigue sin dejar conectarme a las redes inalámbricas.

¿Alguien sabe de una solución a este problema?
Estuve mirando en google y hay varios que al parecer tienen este mismo problema. Ojalá puedan ayudarme.

---

### Post by Lutho on 2010-04-30
me paso eso en acer
solo me reconocio la tarjeta de red, cuando actualize 
todo funciono bien..

$ sudo aptitude update
$ sudo aptitude upgrade

saludo1!

---

