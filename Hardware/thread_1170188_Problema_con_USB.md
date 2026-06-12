---
title: "Problema con USB"
date: 2009-05-26
forum: Hardware
---

### Post by anarko on 2009-05-26
Tengo el siguiente problema, quiero conectar un mp3 MSI pero cuando lo enchufo al puerto USB aparaece como que se conecta y se desconecta probe con todos los puertos USB de la PC y en todos me hace lo mismo tanto los 1.1 como los 2.0. En windows me anda 10 puntos el mp3.

en el dmesg me aparece lo siguiente : 
```
[   58.132020] usb 4-1: new full speed USB device using ohci_hcd and address 2
[   58.305323] usb 4-1: configuration #1 chosen from 1 choice
[   58.325205] Initializing USB Mass Storage driver...
[   58.325313] scsi6 : SCSI emulation for USB Mass Storage devices
[   58.325379] usb-storage: device found at 2
[   58.325382] usb-storage: waiting for device to settle before scanning
[   58.325386] usbcore: registered new interface driver usb-storage
[   58.325388] USB Mass Storage support registered.
[   63.043946] usb 4-1: USB disconnect, address 2

```
Esto mismo aparece en el syslog y en el log del kernel no me da mucha informacion mas que se conecta y desconecta en cuestion de 4 segundos.
Tambien me paso con un disco externo USB pero este duraba unos 2 o 3 minutos antes de desconectarse, otros dispositivos USB andan perfectamente en todos los puertos, es un Ubuntu 9.04.
Probe con todas las configuraciones del bios con respecto al usb y siempre me hace lo mismo.

Saludos.

---

### Post by guillermolisi on 2009-05-26
> **anarko said:**
> Tengo el siguiente problema, quiero conectar un mp3 MSI pero cuando lo enchufo al puerto USB aparaece como que se conecta y se desconecta probe con todos los puertos USB de la PC y en todos me hace lo mismo tanto los 1.1 como los 2.0. En windows me anda 10 puntos el mp3.

en el dmesg me aparece lo siguiente : 
```
[   58.132020] usb 4-1: new full speed USB device using ohci_hcd and address 2
[   58.305323] usb 4-1: configuration #1 chosen from 1 choice
[   58.325205] Initializing USB Mass Storage driver...
[   58.325313] scsi6 : SCSI emulation for USB Mass Storage devices
[   58.325379] usb-storage: device found at 2
[   58.325382] usb-storage: waiting for device to settle before scanning
[   58.325386] usbcore: registered new interface driver usb-storage
[   58.325388] USB Mass Storage support registered.
[   63.043946] usb 4-1: USB disconnect, address 2

```Esto mismo aparece en el syslog y en el log del kernel no me da mucha informacion mas que se conecta y desconecta en cuestion de 4 segundos.
Tambien me paso con un disco externo USB pero este duraba unos 2 o 3 minutos antes de desconectarse, otros dispositivos USB andan perfectamente en todos los puertos, es un Ubuntu 9.04.
Probe con todas las configuraciones del bios con respecto al usb y siempre me hace lo mismo.

Saludos.
Algun otro dispositivo USB que hayas probado y que funcione bien en esa maquina ?
Te pasa solamente con Ubuntu o con algun otro sistema operativo tambien ?

---

### Post by anarko on 2009-05-26
Sin querer sonar molesto, leiste lo que escribi o contestaste por definicion?
Citando mi post original: 

> **anarko said:**
> Tengo el siguiente problema, quiero conectar un mp3 MSI pero cuando lo enchufo al puerto USB aparaece como que se conecta y se desconecta probe con todos los puertos USB de la PC y en todos me hace lo mismo tanto los 1.1 como los 2.0. [COLOR="Red"]En windows me anda 10 puntos el mp3.[/COLOR]

en el dmesg me aparece lo siguiente : 
```
[   58.132020] usb 4-1: new full speed USB device using ohci_hcd and address 2
[   58.305323] usb 4-1: configuration #1 chosen from 1 choice
[   58.325205] Initializing USB Mass Storage driver...
[   58.325313] scsi6 : SCSI emulation for USB Mass Storage devices
[   58.325379] usb-storage: device found at 2
[   58.325382] usb-storage: waiting for device to settle before scanning
[   58.325386] usbcore: registered new interface driver usb-storage
[   58.325388] USB Mass Storage support registered.
[   63.043946] usb 4-1: USB disconnect, address 2

```
Esto mismo aparece en el syslog y en el log del kernel no me da mucha informacion mas que se conecta y desconecta en cuestion de 4 segundos.
Tambien me paso con un disco externo USB pero este duraba unos 2 o 3 minutos antes de desconectarse, [COLOR="Red"]otros dispositivos USB andan perfectamente en todos los puertos[/COLOR], es un Ubuntu 9.04.
Probe con todas las configuraciones del bios con respecto al usb y siempre me hace lo mismo.

Saludos.

---

### Post by staar on 2009-05-26
que modelo exacto es? postea la salida de lsusb, puede ser que alguna regla de udev lo este desconectando...

usa el protocolo MTP para transferir archivos? tiene algún opción o botón de reseteo?

saludos

---

### Post by guillermolisi on 2009-05-26
> **anarko said:**
> Sin querer sonar molesto, leiste lo que escribi o contestaste por definicion?
Citando mi post original:
Upsss ... mil disculpas !! :)

Me concentre en los mensajes de la maquina y pregunte lo primero que me vino a la mente, olvidando lo que habias señalado muy bien vos.

---

### Post by anarko on 2009-05-26
> **staar said:**
> que modelo exacto es? postea la salida de lsusb, puede ser que alguna regla de udev lo este desconectando...

usa el protocolo MTP para transferir archivos? tiene algún opción o botón de reseteo?

saludos

Despacio cerebrito :p, como es eso de regla de udev? y donde me fijo?.

El modelo exacto no lo se, es un mp3 MSI de 512 Mb, cuando lo reconoce el lsusb acusa samsung algo, por unos pocos segundos y despues desaparece, no lo puedo postear ahora porque es la compu de casa y ahora estoy en el laburo.
MTP? ni idea y como lo averiguo. No no tiene ninguna opcion de reseteo.

---

### Post by staar on 2009-05-26
MTP es Media Transfer Protocol (cosa de microchot), en windos usan el Windos Media para transferir, no funcionan como un pendrive normal normal...

tenés que tener instalado libmtp (busca en Synaptic, no creo que el paquete se llame exactamente así) no solo para reconocer el dispositivo, sino también para pasarle temas (con algún programa que soporte el protocolo, como amarok o gnomad2)

después de instalarlo, probá si funciona, si sigue jodiendo, lo siguiente es actualizar el firmware del mp3...

si después sigue jodiendo, postea que la seguimos...

saludos

---

### Post by anarko on 2009-05-26
No, no, nada de MTP, cuando uno lo enchufa es como un pendrive comun y corrientes.
Actulizarle el firmware se me complica, ya que el mp3 es de mi novia y no tengo autoridad legal sobre el :p, por mas que yo se lo regale, y lo peor de todo es que se lo tube que devolver hoy asi que me voya quedar con la duda de cual era el problema. Del problema solo me quedan los recuerdo almacenados proligamente en /var/logs/.

Despejame la duda de la regla del udev que lo desconecte. A que te referis? Todabia no entiendo lo del udev estas cosas nuevas que me complican la vida, soy un viejecito, y aunque hace 10 años que empeze a usar linux, a Linus siempre se le ocurren ideas locas para complicarme la vida, como por ejemplo convertirme el remoto de la plaka de tele en un teclado, quien en su sano juicio va a querer escribir con el control relejos de la tele, yo quiero hacer zapping, se nota que tiene diretibi.

Atento a la respuesta para desasnarme con respecto al udev.

Saludos y gracias.

PD: Escuche mi hdd pero no le entendi nada :p

Edit : El problema es que el dispositivo aparece y desaparece del lsusb y queda como si nada estubiera conectado.

---

