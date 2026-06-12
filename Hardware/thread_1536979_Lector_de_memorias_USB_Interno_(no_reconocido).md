---
title: "Lector de memorias USB Interno (no reconocido)"
date: 2010-07-22
forum: Hardware
---

### Post by atari130xe on 2010-07-22
Hola Foro compré un lector de memorias USB interno (se conecta al puerto USB del mother) y simplemente Ubuntu Lucid NO lo reconoce. Enciende la luz de conectado pero haciendo un ```
lsusb
``` no lo reconoce, alguien tuvo exito o alguna experiencia con estos periféricos? La Marca del Lector es Kelyx
Mi Mother es un Asus M2N sli (AM2)

```
desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
desktop:~$ 

```

---

### Post by guillermolisi on 2010-07-23
Voy a mencionar una obviedad, pero ... estara correctamente enchufado ?
Tenes forma de comprobar eso contra alguna cartilla/manual de instalacion confiable ?

El port USB interno de la placa, estara habilitado por el BIOS ?

---

### Post by atari130xe on 2010-07-23
> **guillermolisi said:**
> Voy a mencionar una obviedad, pero ... estara correctamente enchufado ?
Tenes forma de comprobar eso contra alguna cartilla/manual de instalacion confiable ?

El port USB interno de la placa, estara habilitado por el BIOS ?

Hola Guillermo, no viene con instructivo alguno, solo la caja y los 4 tornillos para sujetarlo al gabinete. El conector del mother tiene una sola posición la luz de power está encendida, pero no es reconocido por el sistema: acabo de dejar la bios con los "default settings" y nada, lo probé en win 7 y el administrador de dispositivos dá "unknown device" y error 43 com que no se cargó correctamente, es un misterio para mi.

---

### Post by guillermolisi on 2010-07-23
En alguna parte figura modelo como para buscarlo en Internet y obtener que chip utiliza ?

Que raro que tampoco funcione en Win.

---

### Post by atari130xe on 2010-07-23
Si es muy raro pero bueno ocurre:

es id+entico a este:
[IMG]http://a.imageshack.us/img707/6381/56131thickbox.jpg[/IMG]

La caja solo Dice:

Lector MEM 8x1 USB (made in China)

---

### Post by euzkoarima on 2010-07-23
Tengo uno igual y me anda (sin haber configurado nada)

a mi el lsusb me tira

> Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Lo único que te puedo decir es que un par de veces, hace ya unos meses, al arrancar no me tomaba el teclado y la luz roja del aparatejo este quedaba prendida (en versión normal prende al ppio pero despues se apaga y queda prendida solo la verde, y roja solo titila si hay acceso).
Tuve que desenchufar de la mother, arrancar, apagar, volver a enchufar en el mismo lugar, prender ... listo todo ok.

Como te dije me lo hizo dos veces. Después nunca más. Así que no se, proba, no perdes nada.

Saludos,
Edudardo

---

### Post by atari130xe on 2010-07-23
> **euzkoarima said:**
> Tengo uno igual y me anda (sin haber configurado nada)

a mi el lsusb me tira



Lo único que te puedo decir es que un par de veces, hace ya unos meses, al arrancar no me tomaba el teclado y la luz roja del aparatejo este quedaba prendida (en versión normal prende al ppio pero despues se apaga y queda prendida solo la verde, y roja solo titila si hay acceso).
Tuve que desenchufar de la mother, arrancar, apagar, volver a enchufar en el mismo lugar, prender ... listo todo ok.

Como te dije me lo hizo dos veces. Después nunca más. Así que no se, proba, no perdes nada.

Saludos,
Edudardo

Hola Eduardo, hoy fuí por si acaso al lugar donde la compré y la probaron con Win XP y funcionaba bien, o sea que no tengo idea de que puede ser, tengo un Mother Asus M2N SLI del 2008 es muy buen Mother para lo que yo necesito. Volví a casa probe a conectarlo nuevamente y nada, solo funciona el puerto auxilar USB que trae la cajita, el lector ni ahi.(La luz roja esta encendida permanentemente en mi caso) Y por ej si inicio el Live DVD de PC-BSD queda en un loop con el puerto USB en cuestión -Error-)

---

### Post by guillermolisi on 2010-07-23
> **atari130xe said:**
> Hola Eduardo, hoy fuí por si acaso al lugar donde la compré y la probaron con Win XP y funcionaba bien, o sea que no tengo idea de que puede ser, tengo un Mother Asus M2N SLI del 2008 es muy buen Mother para lo que yo necesito. Volví a casa probe a conectarlo nuevamente y nada, solo funciona el puerto auxilar USB que trae la cajita, el lector ni ahi.(La luz roja esta encendida permanentemente en mi caso) Y por ej si inicio el Live DVD de PC-BSD queda en un loop con el puerto USB en cuestión -Error-)
No solo lo probaron con WinXP sino que seguramente era otra motherboard, o me equivoco con esta hipotesis ?

---

### Post by atari130xe on 2010-07-23
> **guillermolisi said:**
> No solo lo probaron con WinXP sino que seguramente era otra motherboard, o me equivoco con esta hipotesis ?
No te equivocás Guillermo, otra PC otra Mother...

(pregunto: el servidor de ubuntuforums está lentisimo y se está colgando ultimamente o es mi conexión? -El servidor en ubuntuforums.org está tomando demasiado tiempo para responder... me "canta" Firefox-

---

### Post by alfplayer on 2010-07-23
UF me funciona perfecto, rápido como siempre.

---

### Post by guillermolisi on 2010-07-23
O.T: Despues que Fibertel me cambio el modem, "a las chapas" me funciona todo, UF incluido.

Algo hay en esa motherboard que no quiere reconocer al aparatejo.

---

### Post by euzkoarima on 2010-07-24
Primero que nada debo corregir lo de las luces, lo dije al revés.
Luz Roja: siempre prendida. Cartel "pow" o sea energía.
Luz Verde: prendida solo si se transfieren datos. Cartel "Act".

Te diría de probar dos cosas:

1. Enchufarla en otro puerto interno de USB
2. Confirmar que en la bios no haya algo de USB deshabilitado.

Saludos,
Eduardo

---

### Post by atari130xe on 2010-07-24
> **euzkoarima said:**
> Primero que nada debo corregir lo de las luces, lo dije al revés.
Luz Roja: siempre prendida. Cartel "pow" o sea energía.
Luz Verde: prendida solo si se transfieren datos. Cartel "Act".

Te diría de probar dos cosas:

1. Enchufarla en otro puerto interno de USB
2. Confirmar que en la bios no haya algo de USB deshabilitado.

Saludos,
Eduardo

Bueno me late que puede ser un conflicto de recursos (a pesar de no tener nada más que los puertos "normales" que vienen en el gabinete (4 traseros y 2 frontales) más el puerto interno (único libre). Lo que hice fué desconectar los puertos frontales y en ese conector enchufar la lectora, pero el resultado es el mismo. En cuanto a la BIOS seteé todo a "default" y modifique únicamente lo que si o si debo hacer (sinó no tengo audio por ej. viene con un chip usb de audio (horrible y muy poco compatible) el cual debo deshabilitar porque tengo una placa de audio PCI), al OS lo dejé como "Plug & Play" (antes lo tenía como "No Plug & Play) y a pesar de eso no pasa nada. Sigo investigando.

Les dejo una foto de la mother (les indico cuales son los 2 puertos USB internos (el primero está ocupado con los USB frontales del gabinete)
[IMG]http://a.imageshack.us/img69/2715/asusm2nsliam2pcixddrii.jpg[/IMG]

---

### Post by biale on 2010-07-24
Actualizacion del Bios de la mother ?

---

### Post by atari130xe on 2010-07-24
> **biale said:**
> Actualizacion del Bios de la mother ?

la hice: tenia la version 901 la pasé a la 1002 que es actuál, luego la pase a la 5001 (beta) de Marzo del 2010 y anoche la volvi nuevamente a la 1002 de Jul del 2009, todavía no intenté conectarla con la versión 1002 de la BIOS.

---

### Post by biale on 2010-07-24
Tengo entendido que la asignacion de pines a nivel de los conectores USB de las mothers no es totalmente standard. Con que mother anduvo, manual de la mother, y comparar la asignación de pines.

---

### Post by euzkoarima on 2010-07-30
Upss, hace rato que no entraba al foro. En mi pc (donde anda) tengo una Asus P5Q-E, tendría que mirar donde está conectado.

Saludos,
Eduardo

---

### Post by atari130xe on 2010-07-31
> **euzkoarima said:**
> Upss, hace rato que no entraba al foro. En mi pc (donde anda) tengo una Asus P5Q-E, tendría que mirar donde está conectado.

Saludos,
Eduardo

Buenísimo espero me comentes como hiciste, el conector de la lectora tiene una única posición y no hay manera de conectarlo de otra forma a los 2 únicos puertos internos USB del mother.

---

### Post by euzkoarima on 2010-08-01
Bien, la lectora de tarjetas la tengo conectada al USB111_WFG (donde WFG es porque en otros modedos ademas tiene el wifi, en mi mother es solo usb).

Adjunto la pág del manual donde muestra el conector.
Foto de la lectora de frente
Foto del cable conectado al USB de la mother

Datos adicionales:

El lsusb toma la lectora como:

```
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
```

Si pido lsusb -v -d 0bda:0158

```
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x0158 Mass Storage Device
  bcdDevice           51.95
  iManufacturer           1 Generic
  iProduct                2 USB2.0-CRW
  iSerial                 3 20060413092100000
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 CARD READER
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              5 Bulk-In, Bulk-Out, Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```

Si inserto una tarjeta sd la monta y en dmesg sale

```
[ 1553.580020] usb 1-6: reset high speed USB device using ehci_hcd and address 2
[ 2314.710439] sd 6:0:0:0: [sdb] 3854336 512-byte logical blocks: (1.97 GB/1.83 GiB)
[ 2314.711184] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2314.712558] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2314.712561]  sdb: sdb1
```

Lo que si, acabo de notar algo : si monto la tarjeta y en nautilus la desmonto con botón derecho "expulsar" todo bien. Pero si elijo "expular unidad de forma segura" ahí se boludea y no monta más nada hasta reniciar la pc (cerrar sesión y volver a abrir no funciona).
En dmesg no noto nada distinto al hacerlo de una manera u otra.

Saludos,
Eduardo

---

