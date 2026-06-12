---
title: "LIRC can not work wiyh mce usb remote clone(CLLRCMCE)"
date: 2008-10-24
forum: General Help
---

### Post by pepe1234567890 on 2008-10-24
Hi guys,

I have purchased a cheap Vista MCE clone remote by RF(2.4GHz). The remote is Conceptronic [**CLLRCMCE**]("http://www.conceptronic.net/site/desktopdefault.aspx?tabindex=0&tabid=200&Cat=70&grp=7020&ar=461&Prod_ID=2304&Prod=CLLRCMCE"). The conceptronic Web say that is "Windows Vista® certified product"


This is how the device is reported.
	$lsusb
	*Bus 001 Device 004: ID 1784:0004*
it don't show the Manufactured but i deduced it from this device show where connect the remote. ¿is it correct that there isn't description?

I did that the seccion "[Adding support for more remotes]("https://help.ubuntu.com/community/InstallLirc/Hardy")" say in "InstallLircHardy". But i can not get this remote to work.
	File lirc_mceusb2.c including the remote:
		VENDOR_CONCEPTRONIC 0x1784
		....
		{ USB_DEVICE(VENDOR_CONCEPTRONIC, 0x0004) },
		.....


I can run lirc: "sudo /etc/init.d/lirc restart" and dont problem. Where test a few buttons by command "irw" the daemon dontwork and the Syslog write:

lircd-0.8.2-CVS[5292]: lircd(userspace) ready
lircd-0.8.2-CVS[5292]: accepted new client on /dev/lircd
lircd-0.8.2-CVS[5292]: *could not get file information for /dev/lirc0*
lircd-0.8.2-CVS[5292]: default_init(): No such file or directory
lircd-0.8.2-CVS[5292]: caught signal

:confused::confused:

Thanks you
Ubuntu Hardy 8.04
Mythtv

---

### Post by pepe1234567890 on 2008-10-27
nobody? snify!!!

---

### Post by nastiliano on 2009-01-07
> **pepe1234567890 said:**
> nobody? snify!!!

Hola Pepe.

Perdona por escribir directamente en español, pero he visto tu nick y parece que puedas entenderlo, sinó ya miraría de escribir en inglés (bueno mi péssimo inglés...)

Yo también estoy interesado en un mando para poder controlar mi 'Ubuntu', pero creo que esta opción (Conceptronic CLLRCMCE), no es la mas adecuada, y te diré porqué.
Hace tiempo que me estoy empapando con el tema de mandos via infrarojos y, para empezar, este mando no es de infrarojos, emite por radiofrecuencia. Por tanto, el proyecto de controlador de infrarojos de 'linux' (LIRC) se nos va al garete. O sea, deberíamos buscar unos controladores(drivers) compatibles con el chip que lleva el emisor/receptor USB.

De todas maneras, he enviado un correo electrónico a los de 'Conceptronic'. A ver si se dignan a contestar. Y si contestan, seguro que no quieren saber absolutamente nada de 'linux' pero bueno... algun gurú o información encontraríamos por la red de redes.

¡Saludos!

---

### Post by DefineByte on 2009-01-07
Do you get any response from the remote's buttons while running irw in a terminal window?

Can you post the result of the command ```
ls /dev/input/by-id
```
with the remote's receiver plugged in?

---

### Post by jurr on 2009-01-12
maybe the solution is similar to:

iMON 2.4G DT/LT

The asccociation process of the iMON 2.4G DT/LT remote.

Due to the design (could probably have been better), an application needs to have an open connection to the lirc-daemon*, to allow the association process to start.

To associate the remote you need 2 terminals.

1 To:
    Find the "sys" entry and start the association process
2 To:
    Start a process that has a connection open to the lirc-daemon

The example is shown for bash but sould be quite easy to adapt for (t)csh

 Term #1                                    | Term #2
--------------------------------------------+----------------------------------------
# file=`find /sys -name associate_remote`   |
                                            |# irw
# echo > $file                              |
--------------------------------------------+----------------------------------------

Then you hold down a button on the remote. And soon the "irw" process should start to spit out keycodes. Just stop (Ctrl-C) the "irw" process, and you should be good to go.
*) This is because the USB device connection is only initialized when the lirc-daemon gets a connection to an application, and when it is closed, the USB device connection gets closed too. So only in this period it is possible to send packages to the usb-device.

---

