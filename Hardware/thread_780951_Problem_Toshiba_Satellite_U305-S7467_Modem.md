---
title: "Problem Toshiba Satellite U305-S7467 Modem"
date: 2008-05-03
forum: Hardware
---

### Post by Gcentenari on 2008-05-03
Hola a todos...

Tengo una Toshiba Satellite U305-S7467 con Ubuntu 8.04 y no logro hacer andar el modem de toshiba, en windows aparece como:
standard 33600 bps modem
standard modem
TOSSHIBA software modem

se que no sirve mucho lo que puse, pero espero que me guien un poco.
Muchas Gracias

---

### Post by Hei Ku on 2008-05-03
en ubuntu, pone en una terminal lspci y postea el resultado. asi vamos a tener algo de info seria para ayudarte.

---

### Post by Gcentenari on 2008-05-03
Resultado del lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
04:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
0a:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0a:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

Gracias por la pronta respuesta

---

### Post by Hei Ku on 2008-05-03
la mala noticia es que no se lo ve por ningun lado. proba con lsusb, quizas ahi aparezca.

---

### Post by Gcentenari on 2008-05-04
Resultado de lsusb

Bus 007 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0458:0036 KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


Teclado, FingerPrint y Mouse.... yo no lo veo.:(

---

### Post by Gcentenari on 2008-05-04
Buscando... econtre esto.... no lo puedo creer....

[http://linux.toshiba-dme.co.jp/linux/eng/reference.htm](http://linux.toshiba-dme.co.jp/linux/eng/reference.htm)

Transcribo...

There are 3 different integrated modems used in Toshiba Note PCs.
1.
	Hardware Modem
	Hardware Modem is mostly integrated in the earlier models. It is recognized through its serial port. It works with Linux without any trouble.
2.
	Software Modem (DSP type)
	It is the earlier version of the software modem. Usage is made possible by downloading firmware(F/W) in the DSP. It works with Linux with a driver.
3.
	Software Modem (sound chip type)
	This type of modem is integrated in the later models. Conversion (Analog/Digital) is done through the sound chip and everything is processed in the CPU. This modem does not work with Linux at all.
	 
About releasing development information for software modem (sound chip type)
  	In order to connect a modem to a line, authorization (the line specification)
in its country must be obtained. For the case of hardware modem, authorization
was obtained by the modem chip (IC). For the case of DSP type software modem,
the authorization was obtained by the combination of DSP chip (IC) and the F/W.

Authorization for the sound chip type software modem was obtained for Windows use,
and in order to obtain additional authorizations (supported by most countries
just like the one for Windows) for Linux, it requires tens of millions of yen,
and at least 6 months of processing time. Therefore, considering it from a
business stand point, TOSHIBA is unable to achieve this issue.

It is against the law to use the modem without the above explained authorization.
Therefore, TOSHIBA is unable to release any document for the development purpose.

If you have the software modem (sound chip type) integrated in your TOSHIBA
note PC, please use the external modem with serial port connection, or the
PC card type. Also, please keep in mind that some of the PC card modem
is software modem which would not work with Linux.

...
INCREIBLE !!!

---

### Post by santiagogaitan@gmail.com on 2008-12-14
Hola Gabriel.

Tengo la misma U305 que tú. Desde hace tiempo ya le instalé el Hardy 8.04 64bits. Todo quedó reconocido a excepción del lector biométrico (que nunca usé ni creo que vaya a usar).

He sentido que mi conexión inalámbrica es mucho más lenta aquí en Hardy que en el Vista.

Parace ser que el LAN en nuestra S7467 está soportado por el mismo chip que controla el audio (Realtek RTL-8101 Fast Ethernet Driver). Fuí a la página oficial de Realtek ([http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)) y encontré que tienen un driver para Linux que incluye un Readme con las instrucciones de instalación, así que lo instalé. Sin embargo no sentí mejoras en la velocidad de conexión en comparación con el driver que quedó instalado automáticamente con Hardy.

El wireless de la S7467 está soportado por el chip Intel Corporation PRO/Wireless 4965 AG or AGN Network. También estuve en la página oficial de Intel, allí me redireccionaron a esta página: 

[http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/)

Allí comentan que los drivers para el chip Intel Corporation PRO/Wireless 4965 AG or AGN Network han sida ya incluídos en la línea principal del kernel 2.6.24, que es sobre el que corre Hardy.

Si tú u otra persona conoce una manera de mejorar el desempeño del wireless de este esta laptop estaría muy agradecido.

Otro asunto que noto en esta laptop cuando uso Hardy 8.04 64bits sin conexión del AC power es la poca vida de la batería. Actualmente tengo activado el Frecuency Scaler de Gnome haciendo que mis dos procesadores corran al mínimo de 1Ghz cada uno. Sin embargo la cantidad de tiempo que puede mantenerse la batería es considerablemente menos de lo que en windows (prácticamente la mitad!).

Quedo atento de cualquier ayuda,

Santiago.

---

### Post by faktorqm on 2008-12-15
Les recomendaria a los dos que probaran el 8.10, la parte de energia esta muy trabajada y se solucionaron bastantes problemas, y a su vez el soporte de drivers a notebooks.
Santiago, si te tomo todo menos el bionetrico, como te reconoce a vos el modem? Por lo que posteo del sitio en ingles, yo creeria que la primera opcion o la segunda a mas tardar es la correcta. Si es la tercera... estamos fritos! Salu2!

---

### Post by santiagogaitan@gmail.com on 2009-01-11
Hola faktorqm. No te entendí bien la pregunta. El modem de mi máquina (el wireless y la tarjeta de red) funcionaron con la instalación fresca directamente del livecd. Hice una instalación de un driver de la página de realtek, pero como comenté anteriormente, no he sentido mejoras en la velocidad de conexión wireless. 

El lector biométrico al que me refiero es aquel que en vista te lee las huellas digitales, de modo que puedes usarlas en vez de contraseñas.

Hasta pronto.

---

### Post by santiagogaitan@gmail.com on 2009-01-11
Hola faktorqm. No te entendí bien la pregunta. El modem de mi máquina (el wireless y la tarjeta de red) funcionaron con la instalación fresca directamente del livecd. Hice una instalación de un driver de la página de realtek, pero como comenté anteriormente, no he sentido mejoras en la velocidad de conexión wireless. 

El lector biométrico al que me refiero es aquel que en vista te lee las huellas digitales, de modo que puedes usarlas en vez de contraseñas.

Hasta pronto.

---

### Post by Hei Ku on 2009-01-11
Hay soporte para el lector de huellas (salvo que el biometrico te tome el peso y la impresion infrarroja de la cara :D )

Para eso tendriamos que saber cual es. Pone lsusb en la consola, a ver si aparece.

---

