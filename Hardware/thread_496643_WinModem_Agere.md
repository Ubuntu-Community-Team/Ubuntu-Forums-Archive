---
title: "WinModem Agere"
date: 2007-07-09
forum: Hardware
---

### Post by angeldariodelapuente on 2007-07-09
Kubuntu 7.04

Hola a todos, tengo este problema no puedo cargar los modulos del modem, y eso que las instrucciones son sencillas.

```
Please note that this software is distributed under the Agere Systems Soft
Modem End User SOFTWARE LICENSE AGREEMENT, which can be found in the file
LICENSE, included in this package

Please note that this version of the driver is intended to work Mandrake 10.1 
having Linux kernel version 2.6.8.1-10mdk*.

INSTALLING THE AGERE SOFT MODEM DRIVER VERSION 2.1.40.3.Mandrake 
from the sandard driver package ( zip / tar.gz archieve)

Step 1
Uninstall any older version of the Agere soft modem driver by running 
"make uninstall" from the directory containing the previously installed 
Agere softmodem driver.

Step 2
To install the Agere soft modem driver in LINUX, extract the driver package
(unzip /tar -xzvf) in a directory under Linux and run "make module" and then
"make install" from the command prompt.  This will install both the Agere soft
modem controller driver agrmodem.ko and the Modem serial interface driver
agrserial.ko.
To install the modem driver you must be logged in as root.

Step 3
To use Agere soft modem using KPPP choose "/dev/modem" as the modem device.

To use the Agere soft modem, you can configure "minicom" for the modem device.
Enter "minicom -s" at the command prompt.
Choose "Serial Port Setup"
For "Serial Device" choose "/dev/modem"
Save settings as default (dfl) and start using the modem with minicom.

UNINSTALLING THE MODEM DRIVER

Following are the steps to follow to uninstall the Agere soft modem driver for
Linux.

Step 1
To uninstall the Agere soft modem driver in LINUX, you can run "make uninstall"
from the command prompt. To uninstall the modem driver you must be logged in as
root.

```

Cuando tiro el primer comando "make module" se me traba y salta este error en la consola:

```
dario@AthlonX25600Kubuntu704:~/Programas/agrsm-20070704/agrsm$ sudo make module
Password:
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/dario/Programas/agrsm-200707
04/agrsm modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.o
/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.c:21:26: error: linux/co
nfig.h: No existe el fichero ó directorio
/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.c: En la función ‘SetAgr
ModemInterface’:
/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.c:103: aviso: declaració
n implícita de la función ‘inter_module_get_request’
/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.c:103: aviso: la asignac
ión crea un puntero desde un entero sin una conversión
/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.c:106: aviso: declaració
n implícita de la función ‘inter_module_put’
/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.c: En la función ‘modem_
init_module’:
/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.c:136: aviso: declaració
n implícita de la función ‘inter_module_register’
/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.c: En la función ‘modem_
cleanup_module’:
/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.c:148: aviso: declaració                                                                                                                          n implícita de la función ‘inter_module_unregister’
/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.c: En la función ‘x_requ                                                                                                                          est_irq’:
/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.c:223: aviso: se pasa el                                                                                                                           argumento 2 de ‘request_irq’ desde un tipo de puntero incompatible
/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.c:367:53: error: la macr                                                                                                                          o "INIT_WORK" recibió 3 argumentos, pero solamente tomó 2
/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.c: En la función ‘x_task                                                                                                                          _queue_init’:
/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.c:367: error: ‘INIT_WORK                                                                                                                          ’ no se declaró aquí (primer uso en esta función)
/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.c:367: error: (Cada iden                                                                                                                          tificador no declarado solamente se reporta una vez
/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.c:367: error: ara cada f                                                                                                                          uncion en la que aparece.)
/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.c:366: aviso: variable ‘                                                                                                                          x_tqueue’ sin usar
make[2]: *** [/home/dario/Programas/agrsm-20070704/agrsm/agrsoftmodem.o] Error 1
make[1]: *** [_module_/home/dario/Programas/agrsm-20070704/agrsm] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [module] Error 2
dario@AthlonX25600Kubuntu704:~/Programas/agrsm-20070704/agrsm$
```

Y ahi me trabo nose que mas hacer.

Saludos!

---

### Post by Al_maverick on 2007-07-09
el log que posteaste salio cortado, podes ponerlo de vuelta?

para hacer make module no deberia hacerte falta correrlo como sudo, para el make install. proba eso tambien, aunq no creo q haga diferencia.

---

### Post by angeldariodelapuente on 2007-07-10
Hola! No funciona porque esta echo para Linux kernel version 2.6.8.1-10mdk*. :(. Que bajon alguien sabe que driver meterle, es un modem Encore que en la caja dice "powered by AGERE", paso el scanmodem.

```
Only plain text email is forwarded by the  DISCUSS@linmodems.org List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 7.04  kernel 2.6.20-15-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org .
 Local Linux experts can be found through: http://www.linux.org/groups/index.html
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 7.04 
Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007
 scanModem update of:  2007_June_19


ALSAversion 1.0.13
USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 04:01.0	11c1:0620	11c1:0620	Communication controller: Agere Systems Unknown device 0620

 Modem interrupt assignment and sharing: 
 14:       1893          1   IO-APIC-edge      ide0

 --- Bootup diagnositcs for card in PCI slot 04:01.0 ----

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:14.2	1002:4383	1019:2180	Audio device: ATI Technologies Inc SB600 Azalia

 Modem interrupt assignment and sharing: 
 16:       4307          1   IO-APIC-fasteoi   ohci_hcd:usb1, HDA Intel

 --- Bootup diagnositcs for card in PCI slot 00:14.2 ----
[   17.904000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

1002:4383 is a High Definition Audio card, possibly hosting a soft modem.
 For candidate modem in PCI bus:  00:14.2
   Class 0403: 1002:4383 Audio device: ATI Technologies Inc SB600 Azalia
      Primary PCI_id  1002:4383
    Subsystem PCI_id  1019:2180 
    Softmodem codec or Vendor from diagnostics: 
                              from    Archives: 
                        

 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic 
 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:	

Support can likely be achieved through two mutually exclusive alternatives:
1) An ALSA modem driver plus slmodemd.  Read Smartlink.txt for details, and
to test get the package SLMODEMD-1.0.13.tar.gz from:  
	http://linmodems.technion.ac.il/packages/smartlink/
2) The hsfmodem software for Conexant chipset modems: Read Conexant.txt

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-intel8x0m
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from http://linmodems.technion.ac.il/packages/smartlink/ 
 the package SLMODEMD-1.0.13.tar.gz having a compiled slmodemd. Unpack under Linux with:
 	$ tar zxf SLMODEMD-1.0.13.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
 	sudo slmodemd -c YOUR_COUNTRY --alsa modem:1 
 reporting dynamic creation of ports:
	/dev/ttySL0 --> /dev/pts/N   , with N some number
 Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.


The diagnostic outputs for this softmodem section have their raw information in
folders and text files under /proc/asound/ which you can browse. The information
is from files:
	/proc/asound/pcm
-------------------------------
00-02: ALC883 Analog : ALC883 Analog : capture 2
00-01: ALC883 Digital : ALC883 Digital : playback 1
00-00: ALC883 Analog : ALC883 Analog : playback 1 : capture 2

	/proc/asound/modules
-------------------------------
 0 snd_hda_intel
and from the command:
	aplay -l | grep -i modem


----------------end Softmodem section --------------

scanModem could not identify the Support Type needed from diagnosics or archives.
	If an alternative boot into Microsoft windows can be done, do mouse
clicks on:
   Start > Settings > Control Panel > Classical View (for Window XP) > System
> Hardware > Device Manager > Modems > Click on the + > Modem. Double click to
expand the graphic. Manufacturer information may be displayed. For example, CXT
stands for Conexant. Click the Diagnostics Tab. Record any hardware ID or vendor
and device information.
Next do the Query Modem and record the ATI specifications displayed such as:
    ATI3 - Agere SoftModem Version 2.1.22
    ATI5 - 2.1.22, AMR Intel MB, AC97 ID:SIL REV:0x27
Try to identify the modem setup file, with name perhaps MODEM.INF.
If may contain chipset Vendor informaton.


 Freeware support may be available for a few Conexant chipset modems 
 with support confirmed only for the PCI_id chipset  14f1:2f00.
 See  http://ubuntuforums.org/showthread.php?t=180632

 Otherwise formal support for Conexant chipset modems are available ONLY through 
 http://www.linuxant.com/drivers.  Read Conexant.txt for details.
 and Modem/YourSystem.txt for follow through guidance.  Driver speed is limited to
 14,400 until a key is purchased.  There is NO freeware alternative.
 There are two support package types: hsfmodem  and hcflinmodem.
 http://www.lorenzobettini.it/linux/LinuxSonyVaioVGN-S5VP_B reports a
 problem and solution in stalling a key, after testing of the free low
 speed download.

 Read Conexant.txt

Writing Conexant.txt

Writing Smartlink.txt
============ end Smartlink section =====================

 For candidate modem in PCI bus:  04:01.0
   Class 0780: 11c1:0620 Communication controller: Agere Systems Unknown device 0620
      Primary PCI_id  11c1:0620
 Support type needed or chipset:	Agere.SV2PP_potentially_supported
 


 Vendor 11c1 is Lucent Technologies with modem technology now under LSI Inc. 
Their Linux  code developer/maintainer is Soumyendu Sarkar. Support for a chipset and its 
 continued maintenance is only initiated at the request of a major chipset buyer,
 or comparable sponsor. Several different  modem chipset types  are produced: 
 with varying support under Linux.
 Device ID  Support        Name           Comment
 ---------  -------------  -----------    -----------------------------
 0480       serial drivers Venus           controller chipset 1673JV7
 0440-045d  martian        Mars/Apollo     DSP (digital signal processing) chipsets
 0462       none           56K.V90/ADSL Wildwire 
 048d none           	   SV2P            soft modem 
 048(c or f) AGRSM         SV2P            soft modem
 0600       none           soft modem, very few in the field.
 0620       AGRSM          Pinball  soft modem, in some HP desktop PCs
 062(1-3)   none           SV92PP,Pinball  soft modem, in some HP desktop PCs

martian - At http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/

AGRSM - At http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/ 
agrsm-alpha.tar.bz2 potentially provides support for PCI_id chipsets
   11c1:048c,  11c1:048f and 11c1:0620
in addition to prior support of Subsystems under Intel 8086:???? below
11C1:048C
11C1:048F
11C1:0620
8086:(2416 2426 7196 2486 24C6 24CD6 266D) are soft modem controllers, better
   supported through ALSA modem drivers and the Smartlink slmodemd helper.
   
There has only been one reported success for 11c1:048c, 11c1:048f and 11c1:0620. See:
http://linmodems.technion.ac.il/bigarch/archive-seventh/msg00849.html
http://linmodems.technion.ac.il/bigarch/archive-seventh/msg00970.html
Interaction with experts will likely be necessary to get any of these modems working.

-------------- end Agere Systems section -------------------

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2

 Kernel-header resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	 linux-headers-2.6.20-15-generic


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269224 2007-04-05 00:41 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html

Read Modem/YourSystem.txt concerning other COMM channels: eth0 eth0:avah
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/10-local.rules:#ltmodem
/etc/udev/rules.d/10-local.rules:  KERNEL="ttyLTM0", SYMLINK="modem"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:
ltmodem
--------- end modem support lines --------


```

---

### Post by angeldariodelapuente on 2007-07-26
Che no me enojo si alguien me ayuda heeee

---

### Post by Hei Ku on 2007-07-26
evidentemente nadie tiene un modem similar. Probaste con el soporte de Agere, a ver que responden? La mejor manera de conseguir soporte para Linux es romperles las ****** a los fabricantes de hardware para que sepan que hay usuarios de linux y que tienen que dar soporte.

---

### Post by kowal on 2007-07-26
> **angeldariodelapuente said:**
> Che no me enojo si alguien me ayuda heeee

No creo que sea la forma correcta de pedir ayuda (o al menos NO es la forma más efectiva). 

Ni siquiera sabés que modelo es tu modem! así se complica un poco ayudarte. Googlea por el número del chip o averiguá bien el modelo y seguro vas a encontrar información o un camino..  y así va a ser más sencillo ayudarte.

---

### Post by RJQ on 2007-07-26
Sabes yo he tratado de hacer todo lo que me es posible para que Feisty trabaje con mi winmodem y no he tenido suerte, mi Dapper trabaja de lujo, tal vez si lo pruebas tengas mejor resultado que con Feisty, este parece ser un problema de el Kernel y su asimilación con los drives mas que con los que manufacturan los de  por si ineficientes modems, osea nos dejaron atrás tanto éstos como los desarolladores de Linux :(

una vez mas prueba con Dapper.

---

### Post by v1ncent on 2007-07-27
Leí por ahí que para Gutsy (ubuntu 7.10) van a implementar formas mas faciles de instalar drivers para WinModems de forma manual... Tambien hay un proyecto oficial de Ubuntu para añadir drivers de WinModems en lo que serian los "restricted extras", es decir, agregan los drivers que necesitas, pero los tienes que instalar con 2 clicks.


Tengo que averiguar bien, lo leí muchas veces en los foros oficiales, en launchpad y en los resumenes de noticias de Ubuntu, pero no sé exactamente como hay que hacer para agreguen mis drivers.

Por ahora yo uso el USB Modem Amigo CA-80U, que es un parto a la hora de usar con ubuntu, pero encontré la forma de instalarlo, aunque no sé si va a funcionar siempre correctamente, puede que de golpe simplemente dejen de andar por alguna que otra actualizacion.

En fin, suerte!

---

### Post by RJQ on 2007-07-28
[B][I]
Support type needed or chipset: 

Support can likely be achieved through two mutually exclusive alternatives:
1) An ALSA modem driver plus slmodemd.  Read Smartlink.txt for details, and
to test get the package SLMODEMD-1.0.13.tar.gz from:  
        [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
2) The hsfmodem software for Conexant chipset modems: Read Conexant.txt

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-intel8x0m
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 
 the package SLMODEMD-1.0.13.tar.gz having a compiled slmodemd. Unpack under Linux with:
        $ tar zxf SLMODEMD-1.0.13.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
        sudo slmodemd -c YOUR_COUNTRY --alsa modem:1 
 reporting dynamic creation of ports:
        /dev/ttySL0 --> /dev/pts/N   , with N some number
 Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.


The diagnostic outputs for this softmodem section have their raw information in
folders and text files under /proc/asound/ which you can browse. The information
is from files:
        /proc/asound/pcm[/I][/B]

Ahora que leo un poco mas veo que el scanmodem te da una recomendacion, aqui te menciona los pasos a seguir y aun que no te asegura que funcione te dice que es posible que si, ocupas descargar el archivo que te dice ahi y seguro seguir las instrucciones que vengan con el archivo, se supone que los documentos "Modem,txt y YourSystem.txt" te deben dar mas pasos a seguir.
si tienes problemas leyendo el texto en ingles dejalo saber y te damos una mano.
salud!!

---

### Post by Chilongola on 2007-07-28
Let's see!!  Yo tengo un agere que vino en una caja que dice "NEXXT".  PCI INTERNAL DATA/FAX MODEM 56 KBPS PCI MODEM CARD...  nexxtsolutions.com  

El CD contiene drivers para Fedora, Redhat, y otros pero no para Ubuntu.  Ya pase mas de dos semanas  jugando con esta cosa.  No me doy el brazo a torcer porque lo necesit.  Asi que voy a estar pendiente aqui y voy a hacer "post" lo que me de suerte.
Saludos

---

### Post by RJQ on 2007-07-29
> **Chilongola said:**
> Let's see!!  Yo tengo un agere que vino en una caja que dice "NEXXT".  PCI INTERNAL DATA/FAX MODEM 56 KBPS PCI MODEM CARD...  nexxtsolutions.com  

El CD contiene drivers para Fedora, Redhat, y otros pero no para Ubuntu.  Ya pase mas de dos semanas  jugando con esta cosa.  No me doy el brazo a torcer porque lo necesit.  Asi que voy a estar pendiente aqui y voy a hacer "post" lo que me de suerte.
Saludos

No estoy cien por ciento seguro pero creo que Ubuntu podría funcionar con los drives de Debian, si lo ves enlistado pruebalos si no intenta el scanmodem haber que sugiere, y bienvenido a la batalla por la sobre vivencia de los modems en Ubuntu :popcorn:

---

### Post by Chilongola on 2007-08-30
Despues de batallar por 6 semanas con el modem y mi scanner compre un Cnet 5614XR y trabaja de maravilla.  Tambien compre un pctel "internal"  Ambos el agere y el pctel fueron reconocido y activado en ubuntu pero ni a fregadas pude mandar n recibi fax.  Yo tengo internet por cable asi que no lo quiero para el internet sole para fax.  Nunca me he dado por vencido asi es que voy a probar de nuevo con otra computadora donde voy a poner Ubuntu.

Que se oye sobre el rumor de que sale una nueva version en Octubre que si va tener "drivers" para los winmodems???

---

### Post by angeldariodelapuente on 2007-08-31
Yo al final termine poniendo un SmartLink PCI anda de "**** madre" en ubuntu.

Saludos!

---

### Post by rojojuan on 2007-08-31
> **angeldariodelapuente said:**
> Yo al final termine poniendo un SmartLink PCI anda de "**** madre" en ubuntu.

Saludos!

Tengo en Agere-Lucent con todos los problemas que aquí se comentan...por eso en otro post pedí me dijeran que modem pci podría comprar.
Ese SmartLink anda bien con el fax?

---

### Post by angeldariodelapuente on 2007-08-31
Hola de nuevo nose si con fax andara pero como modem para internet funciona barbaro.

Saludos!

---

### Post by rojojuan on 2007-08-31
> **angeldariodelapuente said:**
> Hola de nuevo nose si con fax andara pero como modem para internet funciona barbaro.

Saludos!

Muchas gracias por la respuesta!

---

### Post by scrooge_74 on 2008-12-21
Es un simple problema de que el driver no tiene capacidad para fax, por ejemplo el winmodem de mi laptop, puede enviar fax, pero no recibe las llamadas

---

