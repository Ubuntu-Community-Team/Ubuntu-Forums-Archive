---
title: "¿Cómo hacer funcionar wireless en ubuntu 9.04?"
date: 2009-08-24
forum: Hardware
---

### Post by Maciett on 2009-08-24
Hola a todos.

Migré hace poco a ubuntu 9.04. Uso un notebook Packard Bell EasyNote s18. Tiene aparte instalado winxp. 

En windows la wireless es reconocida sin problemas y funciona con normalidad. En ubuntu tengo la impresión de que no detecta la tarjeta. No sale la opción de red inalámbrica en los íconos de la izquierda del reloj.

He buscado en internet y solo he encontrado usuarios con el mismo problema, mas no soluciones.

Algunos datos extra

Si tipeo en la consola 

lspci |grep Ethernet && lspci |grep Wireless && lspci |grep Network

Me sale

00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Tengo el archivo original del driver de la tarjeta en .inf y .sys

Instalé ndiswrapper, pero me dice que los drivers son inválidos.

Gracias a todos los que puedan ayudarme desde ya.

---

### Post by Carlos C on 2009-08-24
Por favor escribe en el terminal:
```
lspci
```y copia acá todo lo que te salga. También escribe:
```
iwconfig
```y pega acá lo que aparezca.

Movido a "Hardware".
Saludos.

---

### Post by Maciett on 2009-08-24
Gracias por responder Carlos C.

Si pongo lspci sale

00:01.0 Host bridge: Advanced Micro Devices [AMD] CS5536 [Geode companion] Host Bridge (rev 31)
00:01.1 VGA compatible controller: Advanced Micro Devices [AMD] Geode LX Video
00:01.2 Entertainment encryption device: Advanced Micro Devices [AMD] Geode LX AES Security Block
00:0c.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
00:0c.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
00:0c.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 ISA bridge: Advanced Micro Devices [AMD] CS5536 [Geode companion] ISA (rev 03)
00:0f.2 IDE interface: Advanced Micro Devices [AMD] CS5536 [Geode companion] IDE (rev 01)
00:0f.3 Multimedia audio controller: Advanced Micro Devices [AMD] CS5536 [Geode companion] Audio (rev 01)
00:0f.4 USB Controller: Advanced Micro Devices [AMD] CS5536 [Geode companion] OHC (rev 02)
00:0f.5 USB Controller: Advanced Micro Devices [AMD] CS5536 [Geode companion] EHC (rev 02)

Y escribiendo en la consola iwconfig obtengo

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

Saludos

---

### Post by Carlos C on 2009-08-26
Ese driver viene incluido en el kernel. Qué te aparece si escribes en el terminal:
```
lsmod| grep 8139
```

---

### Post by Maciett on 2009-09-01
Me aparece

8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp

Pero aún funciona sólo por cable.

Saludos

---

### Post by moreback on 2009-09-01
¿Es idea mía o el driver 8139 corresponde a una tarjeta de red cableada? Tengo la impresión que hace uno años usé una de esas y de wireless no tienen nada.

A lo mejor está inhabilitada con algún switch del computador o el sistema simplemente no te la reconoce. ¿Qué aparece que **Sistema -> Administración -> Controladores de hardware**? ¿Con qué nombre aparece en Windows?

Saludos.

---

### Post by Maciett on 2009-09-01
Hola denuevo.

No te puedo responder acerca del número del driver, no los conozco por esta característica.

El computador tiene un switch para habilitar la wireless, que he tenido el cuidado de tener siempre activo, no está bloqueado desde este.

En el primer post puse que pienso lo mismo que usted, Moreback, el sistema no la reconoce.

En la ventana de Sistema -> Administración -> Controladores de hardware sale un cuadro en  blanco con el enunciado: "No se están usando controladores privativos en este sistema".

En Windows esta bajo el nombre de 802.11 b/g USB Wireless Adapter.

Saludos

---

### Post by moreback on 2009-09-01
Por lo que dices, es un dispositivo USB, entonces hay que usar otro comando para ver las características:

```
lsusb
```

y nos copias lo que te aparece,

Ahora debiera ser más fácil ayudarte.

---

### Post by Maciett on 2009-09-01
Hola a todos...

Con lsusb muestra

```
Bus 001 Device 006: ID 18e8:6206 Qcom 
Bus 001 Device 005: ID 14e1:6000  
Bus 001 Device 004: ID 0424:2503 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Algo importante que deben saber es que no es una tarjeta externa, está dentro del notebook, de fábrica. 

Saludos

---

### Post by moreback on 2009-09-01
De los ID que aparecen, creo que el que corresponde a tu tarjeta es el 18e8:6206 (Qcom), pero no encontré mucha información de drivers para Ubuntu, sólo este resultado:

[http://ubuntuforums.org/showthread.php?t=1016630](http://ubuntuforums.org/showthread.php?t=1016630)

A lo mejor con ndiswrapper funcionaría si es que tienes a mano los drivers para Windows.

Saludos.

---

### Post by Maciett on 2009-09-01
Tengo instalado ndiswrapper, también los archivos de driver de windows y al inicio, antes de postiar acá, leí una guía del mismo y trate de instalarlos. Pero sólo obtuve la frase drivers inválidos en la consola cuando hacía ndiswrapper -l.

netw35g : invalid driver!
netw35g.inf : invalid driver!
w35und.sys : invalid driver!

Por eso estoy pidiendo ayuda ahora. Gracias por entender.

Saludos

---

### Post by Maciett on 2009-09-08
Hola,

En estos días he releido [http://ubuntuforums.org/showthread.php?t=1016630](http://ubuntuforums.org/showthread.php?t=1016630) y efectivamente, linux reconoce esa tarjeta con el mismo nombre que la mía, pero el problema que se plantea en ese foro es que el afectado en windows tampoco le reconoce el dispositivo, corríjanme si entendí mal.

En  mi caso si funciona en winxp. 

Tengo la duda, si la tarjeta es usb, ¿ndiswrapper funciona o existe otro programa para esto?

Saludos

---

### Post by gmunioz on 2009-09-09
Hola mac....:

Tu dispositivo inalambrico es:

Qcom Products

- 802.11b/g Internal USB Module

Y tiene un chip:

Ralink RT2571

Ralink da pleno soporte para GnuLinux

Este es su sitio 

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

---

### Post by Maciett on 2009-09-10
Buena gmunioz, ya bajé los drivers.

Estaban en zip así que los descomprimí y vienen 4 archivos, 1 txt que habla de la licencia, y 3 bin que no se donde meterlos n.nU (imagino que esos son los drivers en binario).

Seguimos en contacto.

Saludos

---

### Post by gmunioz on 2009-09-10
Hola mac...:

Algo has hecho en forma equivocada.

Baje el archivo, es el:

2009_0713-RT73_Linux_STA_Drv1.1.0.3.zip

Tiene dos directorios

WPA_Suplicant-0.5.8

Module

Y tiene cada uno un  readme que dicen:

*****************************************************************

    RT73 a/b/g STA driver interface with WPA Supplicant

                      Ralink Tech Corp.

*****************************************************************



Q0. Contents:

-----------------------

defconfig

driver.h

driver_ralink.c

driver_ralink.h

drivers.c

events.c

Makefile

wpa_supplicant.c

wpa_supplicant_i.h

README

wpa_supplicant_example.conf





Q1. How to compile

-----------------------

The driver interface was developed on wpa_supplicant v.0.5.8.

You can install the WPA Supplicant Free Edition development from website.



	[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

	

After download the package then go to wpa_supplicant directory

Follow the steps..



1.) Copy file "driver_ralink.c" and "driver_ralink.h" we provide to wpa_supplicant directory.

1.1.) Copy files driver.h, events.c, wpa_supplicant.c, wpa_supplicant_i.h we provide to wpa_supplicant directory.

2.) Set driver_ralink configuration as y in the "defconfig" or update to the "defconfig" we provide::



# Driver interface for Ralink rt73 driver

CONFIG_DRIVER_RALINK=y

    

3.) Add wpa_driver_ralink_ops() into wpa_supplicant_drivers() in file "drivers.c" 

    or update to the file "drivers.c" we provide:: 

    

#ifdef CONFIG_DRIVER_RALINK

extern struct wpa_driver_ops wpa_driver_ralink_ops; /* driver_ralink.c */

#endif /* CONFIG_DRIVER_RALINK */

    :

    :

struct wpa_driver_ops *wpa_supplicant_drivers[] =

{ 

#ifdef CONFIG_DRIVER_RALINK

	&wpa_driver_ralink_ops,

#endif /* CONFIG_DRIVER_RALINK */  

}

    

4.) Edit the "Makefile" or update to the "Makefile" we provide::



ifdef CONFIG_DRIVER_RALINK

CFLAGS += -DCONFIG_DRIVER_RALINK

OBJS_d += driver_ralink.o

endif



5.) type $cp defconfig .config

6.) Compile the source code using 'make' command.

    



Q2. How to start wpa_supplicant

--------------------------------

1.) First start rt73 driver.



2.) Edit/Create a configuration file of wpa_supplicant.

   -a)  Set your work directory of wpa_supplicant for sockets

        ctrl_interface = YOUR_WORK_PATH

        

   -b)  Set YOUR_OPENSC_PATH if need be. (e.g. generate certificates)

        opensc_engine_path =/YOUR_OPENSC_PATH/engine_opensc.so

        pkcs11_engine_path =/YOUR_OPENSC_PATH/engine_pkcs11.so

        pkcs11_module_path =/YOUR_OPENSC_PATH/opensc-pkcs11.so



   -c)  Set network configuration. (e.g. WPA/EAP-TTLS)

   

    *** refer to wpa_supplicant.conf in details or related documents ***

    

3.) Manually start wpa_supplicant, 

    type $./wpa_supplicant -c your_config_file -i rausb0 -D ralink



    turn on debug mode,

    type $./wpa_supplicant -c your_config_file -i rausb0 -D ralink -d



Notes:

1.) wpa_supplicant 0.5.8 can not compiler with Redhat Enterprise Linux 5 

	kernel 2.6.18-8.el5xen.  Update Redhat Enterprise Linux 5 kernel to

	current version (kernel-xen-2.6.18-8.1.15.el5xen) can solve it.


Y

* README

*

* Ralink Tech Inc.

* 

* [http://www.ralinktech.com](http://www.ralinktech.com)

*



=======================================================================

ModelName:

===========

RT73(RT2571W) Wireless Lan Linux Driver





=======================================================================

Driver lName:

===========

rt73





=======================================================================

Supporting Kernel:

===================

linux kernel 2.4 and 2.6 series. 

Tested in Redhat 7.3 or later.





=======================================================================

Description:

=============

This is a linux device driver for Ralink RT73 a/b/g WLAN Card.





=======================================================================

Contents:

=============

Makefile.4		    : Makefile for kernel 2.4 series

Makefile.6		    : Makefile for kernel 2.6 series

*.c					: c files

*.h					: header files





=======================================================================

Features:

==========

   This driver implements basic IEEE802.11. Infrastructure and adhoc mode 

   with open or shared or WPA-PSK or WPA2-PSK authentication method. 

   NONE, WEP, TKIP and AES encryption. 





=======================================================================

Build Instructions:  

====================

1> $tar -xvzf RT73_Linux_STA_Drv_x.x.x.x.tar.gz

    go to "./RT73_Linux_STA_Drv_x.x.x.x/Module" directory.

    

2> $cp Makefile.4  ./Makefile       # [kernel 2.4]

    or

   $cp Makefile.6  ./Makefile       # [kernel 2.6]

   

3> [kernel 2.4]

    $chmod 755 Configure

    $make config         # config build linux os version



4> $make all            # compile driver source code

4.1> $make install



5> $cp rt73.bin /etc/Wireless/RT73STA/	    # copy firmware

 

6>  $dos2unix rt73sta.dat

    $cp rt73sta.dat  /etc/Wireless/RT73STA/rt73sta.dat       

    # !!!check if it is a binary file before loading !!!  

    

7> $load                

    #[kernel 2.4]

    #    $/sbin/insmod rt73.o

    #    $/sbin/ifconfig rausb0 inet YOUR_IP up

        

    #[kernel 2.6]

    #    $/sbin/insmod rt73.ko

    #    $/sbin/ifconfig rausb0 inet YOUR_IP up





=======================================================================

CONFIGURATION:  

====================

RT73 driver can be configured via following interfaces, 

i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration file

     (iv)RaConfig



i)  iwconfig comes with kernel.  

ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.

iii)copy configuration file "rt73sta.dat" to /etc/Wireless/RT73STA/rt73sta.dat.

iv) RaConfig is utility for rt73.



Note: 

           

Configuration File : rt73sta.dat

---------------------------------------

# Copy this file to /etc/Wireless/RT73STA/rt73sta.dat

# This file is a binary file and will be read on loading rt.o module.

#

# Use "vi -b rt73sta.dat" to modify settings according to your need.

# 

# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure

# 2.) set Channel to "0" for auto-select on Infrastructure mode

# 3.) set SSID for connecting to your Accss-point.

# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"

# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"

# for more information refer to the Readme file.

# 

# The word of "[Default]" must not be removed

[Default]

CountryRegion=0

CountryRegionABand=7

WirelessMode=0

SSID=AP350

NetworkType=Infra

Channel=0

AuthMode=OPEN

EncrypType=NONE

DefaultKeyID=1

Key1Type=0

Key1Str=0123456789

Key2Type=0

Key2Str=

Key3Type=0

Key3Str=

Key4Type=0

Key4Str=

WPAPSK=abcdefghijklmnopqrstuvwxyz

TxBurst=0

PktAggregate=0

TurboRate=0

WmmCapable=0

AckPolicy=0;0;0;0

BGProtection=0

IEEE80211H=0

TxRate=0

RTSThreshold=2347

FragThreshold=2346

PSMode=CAM

TxPreamble=0

AdhocOfdm=0

FastRoaming=0

RoamThreshold=70



-----------------------------------------------

syntax is 'Param'='Value' and describes below. 



1. CountryRegion=value                                 

	value

		0: use 1 ~ 11 Channel

		1: use 1 ~ 13 Channel

		2: use 10, 11 Channel

		3: use 10 ~ 13 Channel

		4: use 14 Channel

		5: use 1 ~ 14 Channel

		6: use 3 ~ 9 Channel

		7: use 5 ~ 13 Channel

   	 	                                      

2. CountryRegionABand=value      							

	value	

		0: use 36, 40, 44, 48, 52, 56, 60, 64, 149, 153, 157, 161, 165 Channel

		1: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140 Channel

		2: use 36, 40, 44, 48, 52, 56, 60, 64 Channel

		3: use 52, 56, 60, 64, 149, 153, 157, 161 Channel

		4: use 149, 153, 157, 161, 165 Channel

		5: use 149, 153, 157, 161 Channel

		6: use 36, 40, 44, 48 Channel

		7: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165 Channel

		8: use 52, 56, 60, 64 Channel

		9: use 34, 38, 42, 46 Channel

		10: use 34, 36, 38, 40, 42, 44, 46, 48, 52, 56, 60, 64 Channel

       

3. SSID=value                	

	value

		0~z, 1~32 ascii characters.

                    	

4. WirelessMode=value

	value	

		0: 11b/g mixed, 

		1: 11b only, 

		2: 11a only,        //Support in RfIcType=1(id=RFIC_5226) or RfIcType=3(id=RFIC_5225)   

		3: 11a/b/g mixed,   //Support in RfIcType=1(id=RFIC_5226) or RfIcType=3(id=RFIC_5225)

		4: 11g only	        

                    	

5. TxRate=value

	value

		 0: Auto    	//WirelessMode=0~4 	

		 1: 1 Mbps	 	//WirelessMode=0 or 1 or 3

         2: 2 Mbps	 	//WirelessMode=0 or 1 or 3

         3: 5.5 Mbps 	//WirelessMode=0 or 1 or 3

         4: 11 Mbps 	//WirelessMode=0 or 1 or 3

         5: 6  Mbps  	//WirelessMode=0 or 2 or 3 or 4

         6: 9  Mbps  	//WirelessMode=0 or 2 or 3 or 4

         7: 12 Mbps  	//WirelessMode=0 or 2 or 3 or 4

         8: 18 Mbps  	//WirelessMode=0 or 2 or 3 or 4

         9: 24 Mbps  	//WirelessMode=0 or 2 or 3 or 4

        10: 36 Mbps  	//WirelessMode=0 or 2 or 3 or 4

        11: 48 Mbps  	//WirelessMode=0 or 2 or 3 or 4

        12: 54 Mbps  	//WirelessMode=0 or 2 or 3 or 4

 	                                       

6. Channel=value

	value

		depends on CountryRegion or CountryRegionABand

                    	

7. BGProtection=value

	value

		0: Auto 

		1: Always on 

		2: Always off

                    	

8. TxPreamble=value

  	value

		0: Preamble Long

		1: Preamble Short 

		2: Auto

                    	

9. RTSThreshold=value

	value

		1~2347                                                       

                    	                                       

10. FragThreshold=value

	value       	

		256~2346

                    	

11. TxBurst=value

	value

		0: Disable

		1: Enable



12. NetworkType=value	    		

	value 

		Infra: infrastructure mode

       	Adhoc: adhoc mode



13. AdhocOfdm=value

    value

        0: WIFI mode    (1,2,5.5,11 mbps rates)   				   

        1: b/g mixed,   (1,2,5.5,11,6,9,12,18,24,36,48,54 mbps rates)

        2: 11g only,    (6,9,12,18,24,36,48,54 mbps rates) 

        3: 11a only,    (6,9,12,18,24,36,48,54 mbps rates)

        

14. AuthMode=value

	value

		OPEN	 	For open system	

		SHARED	  	For shared key system	

		WEPAUTO     Auto switch between OPEN and SHARED

		WPAPSK      For WPA pre-shared key  (Infra)

		WPA2PSK     For WPA2 pre-shared key (Infra)

		WPANONE		For WPA pre-shared key  (Adhoc)

		WPA         Use WPA-Supplicant

		WPA2        Use WPA-Supplicant



15. EncrypType=value

	value

		NONE        For AuthMode=OPEN                    

		WEP         For AuthMode=OPEN or SHARED 

		TKIP        For AuthMode=WPAPSK or WPA2PSK or WPANONE                 

		AES         For AuthMode=WPAPSK or WPA2PSK or WPANONE                 

		

16. DefaultKeyID=value

	value

		1~4



17. Key1=value

    Key2=value

    Key3=value

    Key4=value

	value

		10 or 26 hexadecimal characters eg: 012345678

        5 or 13 ascii characters eg: passd

    (usage : "iwpriv" only)



18. Key1Type=vaule

    Key2Type=value

    Key3Type=vaule

    Key4Type=vaule

    value

		0   hexadecimal type

		1   assic type

    (usage : reading profile only)



19. Key1Str=value

    Key2Str=value

    Key3Str=vaule

    Key4Str=vaule

    value

		10 or 26 characters (key type=0)

		5 or 13 characters  (key type=1)

    (usage : reading profile only)	

                                                    

20. WPAPSK=value              	

	value

		8~63 ASCII  		or 

		64 HEX characters



21. PSMode=value

    value

    	0: CAM			Constantly Awake Mode

		1: Max_PSP		Max Power Savings

		2: Fast_PSP		Power Save Mode

	

22. IEEE80211H=value

	value

		0:	Disable

		1:	Enable	Spectrum management

	    (This field can be enable only in A band)



23. FastRoaming=value

    value

        0: Disable

        1: Enable Fast Roaming



24. RoamThreshold=value

    vale

        61 ~ 89

        

    This value is a absolute threshold in dBm.

    The condition to roam when receiving Rssi less than (-1*value).



// //////////////////////    																		

//  No Support !!!

// /////////////////////

//  PktAggregate,            

//  TurboRate,																

//  WmmCapable,				

//  AckPolicy

// /////////////////////



MORE INFORMATION

=================================================================================

If you want for rt73 driver to auto-load at boot time:

A) choose rausb0 for first RT73 WLAN card, rausb1 for second RT73 WLAN card, etc.

 

B) go to "./RT73_Linux_STA_Drv_x.x.x.x/Module" directory.

   $make install



NOTE:

	if you use dhcp, 

	add this line

	BOOTPROTO='dhcp'

	in the file ifcfg-rausb0 .





*C) To ease the Default Gateway setting, 

    add the line

    GATEWAY=x.x.x.x   

    in /etc/sysconfig/network



D) When build for SUSE, please unmark the part for SUSE in Makefile.



E) When build for Mandriva 2007.1, please unmark the part for Mandriva in Makefile.

   You have to remove the module pre-loaded by Mandriva 2007.1 before

   you can load our rt73sta module.

   Edit this file /lib/modules/`uname -r`/build/.kernelrelease before "4> make all"

   Change it to 2.6.17-13mdv (should be the same as "uname -r" value)

   Follow "Build Instructions: 4> and 4.1>"  then the driver should be loaded correctly on boot up.

---

