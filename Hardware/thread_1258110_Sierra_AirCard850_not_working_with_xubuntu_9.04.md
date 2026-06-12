---
title: "Sierra AirCard850 not working with xubuntu 9.04"
date: 2009-09-04
forum: Hardware
---

### Post by redcolt on 2009-09-04
Hi alltogether,

my Sierra Wireless AirCard850 does not work with xubuntu 9.04  (kernel 2.6.28-15-generic) on a Panasonic Toughbook CF-72Q (Pentium III 850Mhz).
When I'm using the Novatel Wireless Merlin U530 3G pc-card modem, it works with xubuntu 9.04 "plug and play". Unfortunately, this UMTS-modem does not have an connector for an external antenna. That's why I needed to use the Sierra Wireless AirCard850 pc-card modem. This modem didn't work "plug and play", so I tried this howto from the ubuntu documentation:

[https://help.ubuntu.com/community/AirCard8X0](https://help.ubuntu.com/community/AirCard8X0)

and also this howto from the Sierra Wireless support page:

[http://sierrawireless.custhelp.com/app/answers/detail/a_id/500](http://sierrawireless.custhelp.com/app/answers/detail/a_id/500)

                                 typing "pccardctl ident" in the terminal gave me the following information:


                           > Socket 0:  
   product info: "Sierra Wireless", "AC850", "3G Network Adapter", "R1"  
   manfid: 0x0192, 0x0710  
   function: 6 (network)
Everything looked quite o.k and by typing "modinfo sierra" in the terminal I got this:


                           > filename:       /lib/modules/2.6.28-15-generic/kernel/drivers/usb/serial/sierra.ko  
 license:        GPL  
 version:        v.1.3.2  
 description:    USB Driver for Sierra Wireless USB modems  
 author:         Kevin Lloyd <klloyd@sierrawireless.com>  
 srcversion:     849FEAD771651BE184C5E16 
 alias:          usb:v0F3Dp0112d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p0112d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6892d*dc*dsc*dp*icFFiscFFipFF*  
 alias:          usb:v1199p6891d*dc*dsc*dp*icFFiscFFipFF*  
 alias:          usb:v1199p6890d*dc*dsc*dp*icFFiscFFipFF*  
 alias:          usb:v1199p6880d*dc*dsc*dp*icFFiscFFipFF*  
 alias:          usb:v1199p685Ad*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6859d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6856d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6855d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6853d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6852d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6851d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6850d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p683Ed*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p683Dd*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p683Cd*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p683Bd*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p683Ad*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6833d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6832d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6821d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6820d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v03F0p1E1Dd*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6815d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6813d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6812d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6803d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6804d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p6802d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p0028d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p0027d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p0026d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p0025d*dc*dsc*dp*icFFiscFFipFF*  
 alias:          usb:v1199p0023d*dc*dsc*dp*icFFiscFFipFF*  
 alias:          usb:v1199p0120d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p0021d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p0019d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p0220d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p0024d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p0020d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v03F0p1B1Dd*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p0218d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p0018d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1199p0017d*dc*dsc*dp*ic*isc*ip*  
 depends:        usbserial  
 vermagic:       2.6.28-15-generic SMP mod_unload modversions 586  
 parm:           nmea:NMEA streaming (bool)  
 parm:           debug: debug messages (bool)  
Obviously, there is a sierra driver on my system, but - maybe - the wrong one.
My problems began, when I tried to follow the other instructions of the ubuntu documentation above to install the driver "SW_8xx_SER.dat" being downloaded from the Sierra support page.
I can't find the target, where to install this "SW_8xx_SER.dat" AirCard-driver. There is no "**/etc/pcmcia/config**"-file  and no "*Modems and other serial devices* section:" in it.. And I am unable to find "/lib/firmware/SW_7xx_SER.cis" for overwriting it.
 The instructions above were written in the years 2006/2007. Maybe, something has been changed on Ubuntu since this time.

Can anyone help me to get the AirCard working?

redcolt

---

