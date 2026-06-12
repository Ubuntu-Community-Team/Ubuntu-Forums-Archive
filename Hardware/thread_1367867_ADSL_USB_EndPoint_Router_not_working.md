---
title: "ADSL USB EndPoint Router not working"
date: 2009-12-30
forum: Hardware
---

### Post by mariano_rcia on 2009-12-30
Hi,
I'm quite new to GNU-Linux and I'm having a problem with my ADSL USB EndPoint Router (wan adapter). It's not working, Ubuntu doesn't recognize it, and I think it has something to do with the drivers, which I don't know how to install them.

My box has:

Ubuntu release 9.10 (Karmic)
Kernel 2.6.31-16 generic
GNOME 2.28.1
Intel Core 2 Duo E8200 @ 2.66 GHz
3 Gib RAM
320 Gib HD

The device I'm having trouble with is:

CA85UR ADSL USB EndPoint Router ("Amigo")
Software:110502_Re110c_E
Hardware:HMX-CA85UR-K8 Rev.2


I could manage to find a zipped archive on the net, which I'm uploading and posting the link here.

Also found a pdf manual and a guide (unfortunately they're in Spanish and because of their size I can't upload them here), which I'm posting the links as well:

- Driver Linux:
[http://servicios.arnet.com.ar/arnetonline/drivers/Amigo_Linux.zip](http://servicios.arnet.com.ar/arnetonline/drivers/Amigo_Linux.zip)

- Manual (Spanish):
[http://servicios.arnet.com.ar/arnetonline/pdfs/Usb_AmigoCa85_manual.pdf](http://servicios.arnet.com.ar/arnetonline/pdfs/Usb_AmigoCa85_manual.pdf)

- Installation guide (Spanish):
[http://servicios.arnet.com.ar/arnetonline/pdfs/Usb_AmigoCa85_guia.pdf](http://servicios.arnet.com.ar/arnetonline/pdfs/Usb_AmigoCa85_guia.pdf)

The zip archive (Amigo_Linux.zip) has the following content:

cxacru.c
Kbuild
Kconfig
usbatm.c
usbatm.h

Well, I'm stuck! don't know what to do or how to proceed from here. Is this source code? how do I compile it? How do I go about it? Or is there any other solution to this? I'm clueless. Can anyone help me out here? Many thanks in advance.


The Kbuild file has this content:

#
# Makefile for USB ATM/xDSL drivers
#

obj-$(CONFIG_USB_ATM)		+= usbatm.o
#obj-$(CONFIG_USB_SPEEDTOUCH)	+= speedtch.o
obj-$(CONFIG_USB_CXACRU)	+= cxacru.o



And the Kconfig file this:

#
# USB/ATM DSL configuration
#

menu "USB DSL modem support"
	depends on USB

config USB_ATM
	tristate "USB DSL modem support"
	depends on USB && ATM
	select CRC32
	default n
	help
	  Say Y here if you want to connect a USB Digital Subscriber Line (DSL)
	  modem to your computer's USB port.  You will then need to choose your
	  modem from the list below.

	  To compile this driver as a module, choose M here: the
	  module will be called usbatm.

config USB_SPEEDTOUCH
	tristate "Speedtouch USB support"
	depends on USB_ATM
	select FW_LOADER
	help
	  Say Y here if you have an SpeedTouch USB or SpeedTouch 330
	  modem.  In order to use your modem you will need to install the 
	  two parts of the firmware, extracted by the user space tools; see
	  <http://www.linux-usb.org/SpeedTouch/> for details.

	  To compile this driver as a module, choose M here: the
	  module will be called speedtch.

config USB_CXACRU
	tristate "Conexant AccessRunner USB support"
	depends on USB_ATM
	select FW_LOADER
	help
	  Say Y here if you have an ADSL USB modem based on the Conexant
	  AccessRunner chipset.  In order to use your modem you will need to
	  install the firmware, extracted by the user space tools; see
	  <http://accessrunner.sourceforge.net/> for details.

	  To compile this driver as a module, choose M here: the
	  module will be called cxacru.

endmenu

---

### Post by Project PWNED on 2009-12-30
Try this [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

---

### Post by mariano_rcia on 2009-12-30
Thanks Project PWNED, I'll take a look and report back later. Cheers mate,

---

