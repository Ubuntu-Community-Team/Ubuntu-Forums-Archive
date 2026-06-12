---
title: "HELP .. Compiled kernel module hangs computer.."
date: 2011-02-16
forum: Hardware
---

### Post by arimaniac on 2011-02-16
Hello!

I would like to ask for help please... THANKS IN ADVANCE FOR READING!!!!! :-)

I am in the process of trying to use the old **usbkbd** kernel module to fix the following problem:
I have a barcode reader that SHOULD work using this old driver according to the Ubuntu wiki, and now fails to work:
```

[ 2131.280305] usb 7-2: new low speed USB device using uhci_hcd and address 2
[ 2131.505808] usb 7-2: configuration #1 chosen from 1 choice
[ 2131.535800] generic-usb: probe of 0003:04B4:BCA1.0009 failed with error -22

```

My Ubuntu 10.04: 2.6.32-28-generic i686

Steps i did:
Downloaded the linux source from Ubuntu repo and extarcted the usbkbd.c file.  
I have compiled the driver: usbkbd.ko
```

make -C /lib/modules/2.6.32-28-generic/build M=/home/arimaniac/USBKBD modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-28-generic'
  CC [M]  /home/arimaniac/USBKBD/usbkbd.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/arimaniac/USBKBD/usbkbd.mod.o
  LD [M]  /home/arimaniac/USBKBD/usbkbd.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-28-generic'

```

its modinfo:
```
filename:       usbkbd.ko
license:        GPL
description:    USB HID Boot Protocol keyboard driver
author:         Vojtech Pavlik <vojtech@ucw.cz>
srcversion:     DCBEE877043D871E760AAB2
alias:          usb:v*p*d*dc*dsc*dp*ic03isc01ip01*
depends:        
vermagic:       2.6.32-28-generic SMP mod_unload modversions 586 

```

i copied it to the usb hid modules dir i.e.: /lib/modules/2.6.32-28-generic/kernel/drivers/hid/usbhid/
and installed it with insmod:
```

arimaniac@arimaniac-laptop:~/USBKBD$ sudo insmod /lib/modules/2.6.32-28-generic/kernel/drivers/hid/usbhid/usbkbd.ko
arimaniac@arimaniac-laptop:~/USBKBD$ dmesg | tail
[ 1144.244769] usbcore: registered new interface driver usbkbd
[ 1144.244778] usbkbd: :USB HID Boot Protocol keyboard driver

```

.... and added the module to the initramfs to load on bootup ..  updated the linux image...

and rebooted... now the device is found ...
```

[    1.384074] usb 7-2: new low speed USB device using uhci_hcd and address 2
[    1.558035] usb 7-2: configuration #1 chosen from 1 choice
[    1.575041] input: Guest Barcode Reader as /devices/pci0000:00/0000:00:1d.0/usb7/7-2/7-2:1.0/input/input7

```

SO FAR SO GOOD ... now the problem.... :   :-(

I scan a barcode and the system HANGS:
caps lock key blinks on and off... 
keyboard, mouse, buttons dont work...

have to unplug it from the wall...

already tried blacklisting the usbhid module but it still hangs.
update:
it also hangs when I press the numlock key (but after i login).. 
appears to get itself in an infinite loop...
update:

I FOUND SOME CYPRESS DRIVERS IN THE LINUX KERNEL... ARE THESE RELEVANT????

__A N Y__________I D E A S____?????????????

---

### Post by arimaniac on 2011-02-16
Ok I was wrong about the usbkbd module...
the correct module to load was hid-cypress.

Since I run ubuntu 10.04 with 2.6.32 the barcode reader was not available in the kernel... 

so I patched the hid-cypress.c with: 
```

.
.
.
static const struct hid_device_id cp_devices[] = {
	{ HID_USB_DEVICE(USB_VENDOR_ID_CYPRESS, USB_DEVICE_ID_CYPRESS_BARCODE_1),
		.driver_data = CP_RDESC_SWAPPED_MIN_MAX },
	{ HID_USB_DEVICE(USB_VENDOR_ID_CYPRESS, USB_DEVICE_ID_CYPRESS_BARCODE_2),
		.driver_data = CP_RDESC_SWAPPED_MIN_MAX },
[B]	{ HID_USB_DEVICE(USB_VENDOR_ID_CYPRESS, USB_DEVICE_ID_CYPRESS_BARCODE_3),
		.driver_data = CP_RDESC_SWAPPED_MIN_MAX },[/B]
	{ HID_USB_DEVICE(USB_VENDOR_ID_CYPRESS, USB_DEVICE_ID_CYPRESS_MOUSE),
		.driver_data = CP_2WHEEL_MOUSE_HACK },
	{ }
};
.
.
.

```

and the hid-ids.h with

```

.
.
.
#define USB_DEVICE_ID_CYPRESS_BARCODE_1	0xde61
#define USB_DEVICE_ID_CYPRESS_BARCODE_2	0xde64
**#define USB_DEVICE_ID_CYPRESS_BARCODE_3	0xbca1**
.
.
.

```

as per illustrated by kernel 2.6.37

and repeated compile install and add to start up... 

WORKS LIKE A CHARM ... 


YEAH baby.. .:P

---

### Post by arimaniac on 2011-02-16
oh and the barcode reader device details.....


T:  Bus=06 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=1.5  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04b4 ProdID=bca1 Rev= 2.52
S:  Manufacturer=Guest
S:  Product=Barcode Reader
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

---

