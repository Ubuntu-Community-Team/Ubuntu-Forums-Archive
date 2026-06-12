---
title: "Sony Vaio T1311"
date: 2012-08-25
forum: Hardware
---

### Post by iceman on 2012-08-25
Hi all,
three weeks ago i bought this laptop (exactly SVT1311 or SVT131A11M).
It has Ivy Bridge, i5, Intel HD Graphics 4000, touchpad (MacBookAir style), wireless bluetooth, hybrid SSD/SATA drive (32gb+320gb).
I was able to make Ubuntu boot from SSD (disabling windows "fast partition")
I am using 11.04, i moved my 11.04 Ubuntu OS from "old" laptop to the new one.

I have a lot of problem...

1° Intel HD Graphics 4000 does not work right. I tried updating drivers with "glasen-intel-driver", but hardware acceleration is fuzzy and the only way to have a good experience is to login in Classic mode (without effects). Brightness can not be set, even appending "acpi_osi=Linux acpi_backlight=vendor" on kernel cmdline.

2° Bluetooth does not work at all. lsusb give me this: 0489:e036. Device is visible thru hciconfig -a but it's not able so search device or visible to other device. I'm stuck and i don't how to solve

3° Touchpad is a real problem. I was able to enable two finger scroll and three fingers "click" (it's like pushing both left and right together), but the problem is when i want to drag a window (then pushing and moving finger together). In this situation touchpad catch the "left click" while moving finger to move window like a two finger click (right click). I was not able to solve this issue.


Please, let me know your experience just to solve problems together

P.s. Wireless is not working OOB. I downloaded compat-wireless drivers, compiled, installed, rebooted and blacklisted "acer_wmi" in /etc/modprobe.d/blacklist.conf to make it work under network-manager (remember to enable devices by "rfkill" all)

wget [http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

---

### Post by iceman on 2012-08-25
OK, now i was able to boot 12.04 and i have news: graphics seems perfect and touchpad is sensible better (there is no the problem about drag window!), wireless is working OOB (you have to remove acer_wmi to get network-manager to manage it).
I think i should probably upgrade kernel to 3.2 to make everything work under 11.04... i'll let you know 

The only problem stills remains bluetooth... absolutely not functional, but visible thru hciconfig -a or System Settings->Bluetooth. Unvisible to other device, no new device discovery results...

---

### Post by iceman on 2012-08-27
No way to get bluetooth discovery device (nor pairing!)
Any solution?

---

### Post by iceman on 2012-08-30
Nothing to do, even with 3.5.3 kernel on 12.04 (device 0489:e036)

hciconfig show it, but it can't search or pairing any devices.
I'm stuck.

> hci0:	Type: BR/EDR  Bus: USB
	BD Address: 08:ED:B9:C6:57:56  ACL MTU: 1022:8  SCO MTU: 183:5
	UP RUNNING PSCAN 
	RX bytes:1135 acl:0 sco:0 events:44 errors:0
	TX bytes:918 acl:0 sco:0 commands:40 errors:0
	Features: 0xff 0xfe 0x0d 0xfe 0xd8 0x7f 0x7b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF 
	Link mode: SLAVE ACCEPT 
	Name: 'ubuntu-0'
	Class: 0x6e0100
	Service Classes: Networking, Rendering, Capturing, Audio, Telephony
	Device Class: Computer, Uncategorized
	HCI Version: 3.0 (0x5)  Revision: 0x102
	LMP Version: 4.0 (0x6)  Subversion: 0x1
	Manufacturer: Atheros Communications, Inc. (69)


---

### Post by iceman on 2012-08-31
You all very helpful... ](*,) noone who knows something about this bluetooth card...

---

### Post by iceman on 2012-08-31
OK i made it by myself!
First of all: everything is now working!! EVERYTHING!

BT:
First of all: i'm using 3.2.0-30-generic-pae 32bit kernel. Switch paths to the kernel you are using!

I downloaded kernel source 3.2.0 and copied btusb.c and ath3k.c on a folder (ex: /bluetooth ). Those files were in drivers/bluetooth folder on kernel source.
On btusb.c, after line 143 i put:

 { USB_DEVICE(0x0489, 0xe036), .driver_info = BTUSB_ATH3012 },

On ath3k.c, after line 78 i put:

{ USB_DEVICE(0x0489, 0xe036) },

After that, i created a Makefile on /bluetooth folder with this content:

obj-m = btusb.o
KVERSION = $(shell uname -r)
all:
        make -C /lib/modules/$(KVERSION)/build M=$(PWD) modules

And compiled:

sudo make -C /lib/modules/3.2.0-30-generic-pae/build M=/bluetooth modules

Same thing for ath3k:

obj-m = ath3k.o
KVERSION = $(shell uname -r)
all:
        make -C /lib/modules/$(KVERSION)/build M=$(PWD) modules


And compiled:

sudo make -C /lib/modules/3.2.0-30-generic-pae/build M=/bluetooth modules

Now, you have to move these two .ko modules under your kernel modules folder:
sudo mv *.ko /lib/modules/3.2.0-30-generic-pae/kernel/drivers/bluetooth/

You can reboot or insmod modules, they will be working (obviously you should stop bluetooth service, rmmod btusb and insmod both... but it's easier for you to reboot!!)

Basically this modification blacklist btusb module to handle internal bt and let ath3k to manage upon btusb.
I tried to connect thru my Samsung Galaxy III, and everything went good and files exchange too. I paired my Apple Magic Mouse too without problem!
NICE!!

Thank you to have not helped me!!! :D

P.s. I attached both modules already patched! You can jump to Makefile creation and builds!

---

### Post by iceman on 2012-08-31
Adjusting backlight. How to:

As root, create a file in udev (ex: /etc/udev/rules.d/99-backlight.rules)
and put: 
ACTION=="change", SUBSYSTEM=="backlight", RUN+="/usr/sbin/backlight.sh"

create /usr/sbin/backlight.sh with this content:
```
#!/bin/bash
intelmaxbrightness=`cat /sys/class/backlight/intel_backlight/max_brightness`
acpimaxbrightness=`cat /sys/class/backlight/acpi_video0/max_brightness`
scale=`expr $intelmaxbrightness / $acpimaxbrightness`
acpibrightness=`cat /sys/class/backlight/acpi_video0/brightness`
newintelbrightness=`expr $acpibrightness \* $scale`
curintelbrightness=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ "$newintelbrightness" -ne "$curintelbrightness" ]
then
	echo $newintelbrightness > /sys/class/backlight/intel_backlight/brightness
fi
exit 0

```

"Magically" your Intel HD Graphics 4000 will switch his brightness!

---

### Post by C@illou on 2012-10-07
> **iceman said:**
> Adjusting backlight. How to:

As root, create a file in udev (ex: /etc/udev/rules.d/99-backlight.rules)
and put: 
ACTION=="change", SUBSYSTEM=="backlight", RUN+="/usr/sbin/backlight.sh"

create /usr/sbin/backlight.sh with this content:
```
#!/bin/bash
intelmaxbrightness=`cat /sys/class/backlight/intel_backlight/max_brightness`
acpimaxbrightness=`cat /sys/class/backlight/acpi_video0/max_brightness`
scale=`expr $intelmaxbrightness / $acpimaxbrightness`
acpibrightness=`cat /sys/class/backlight/acpi_video0/brightness`
newintelbrightness=`expr $acpibrightness \* $scale`
curintelbrightness=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ "$newintelbrightness" -ne "$curintelbrightness" ]
then
    echo $newintelbrightness > /sys/class/backlight/intel_backlight/brightness
fi
exit 0

```"Magically" your Intel HD Graphics 4000 will switch his brightness!

First of all, thank you very much for sharing all of this! I have a Vaio T11 (SVT1111C5E) and I have the same issues. For now I just tried to get the brightness working, and I did what you explained here, but it doesn't work. I'm not running Ubuntu but Archlinux with Gnome 3, do you think that could be a significative difference? And also, do you have changed anything else? Like adding boot options? Thanks!

---

### Post by iceman on 2012-10-07
Which kind of video adapter have T11? Intel HD4000 or two video adapters?

---

### Post by iceman on 2012-10-07
Have you make executable /usr/sbin/backlight.sh?

sudo chmod +x /usr/sbin/backlight.sh

---

### Post by C@illou on 2012-10-07
> **iceman said:**
> Which kind of video adapter have T11? Intel HD4000 or two video adapters?
I have an HD4000 only, as you. The CPU is an intel i7 3517u if I recall corectly.

---

### Post by iceman on 2012-10-07
Have you read my last message?

---

### Post by C@illou on 2012-10-07
oops, my bad, I'm confused, I messed up between bin ans sbin :s sorry for bothering you. The good news is it's also working on the vaio T11!

---

### Post by jcfagny on 2012-10-20
Hello,
Same problem with a Vaio SVE1711.
Trying to understand.
You creat a txt (?) file with :

obj-m = btusb.o
KVERSION = $(shell uname -r)
all:
make -C /lib/modules/$(KVERSION)/build M=$(PWD) modules

in the /bluetooth directory (where you put ath3k.c and btusb.c)
and run 

code
sudo make -C /lib/modules/3.2.0-30-generic-pae/build M=/bluetooth modules

with the correct (present) name of the kernel.

and the same for ath3k

I'm right ?

Anyway thanks for help !!!!!!

---

### Post by C@illou on 2012-10-20
Hi, if you're talking about the problem with the bluetooth, the fix has been in the linux kernel since the version 3.5.6 at least, for our computer model (SVT11 and SVT13)

---

