---
title: "intel 3945abg WLAN driver"
date: 2012-04-11
forum: Hardware
---

### Post by guru1988 on 2012-04-11
Hi all,
I am new to linux in my personal life. I just installed Ubuntu 11.10 in my laptop. I got intel 3945abg wlan which is not working. I got many possible solutions from this forum but none seems to be working for me. 


rfkill list all- didn't display anything(no device is listed).

next is i tried to edit the blacklist.conf in the /etc/modprobe.d... 

This is my blacklist.conf file:
[B]# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
#blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac[/B]

And i tried installing ieee 80211-1.2.18 but it returned error to me. 

error message in terminal:
[b]
guru@guru-laptop:~/Downloads/ieee80211-1.2.18$ make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/3.0.0-12-generic for ieee80211 components...
egrep: /lib/modules/3.0.0-12-generic/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/3.0.0-12-generic/build M=/home/guru/Downloads/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
/home/guru/Downloads/ieee80211-1.2.18/Makefile:17: 
/home/guru/Downloads/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/guru/Downloads/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/guru/Downloads/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/guru/Downloads/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/guru/Downloads/ieee80211-1.2.18/ieee80211_module.o
/home/guru/Downloads/ieee80211-1.2.18/ieee80211_module.c: In function &#8216;alloc_ieee80211&#8217;:
/home/guru/Downloads/ieee80211-1.2.18/ieee80211_module.c:148:5: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/guru/Downloads/ieee80211-1.2.18/ieee80211_module.c:149:5: error: &#8216;struct net_device&#8217; has no member named &#8216;change_mtu&#8217;
/home/guru/Downloads/ieee80211-1.2.18/ieee80211_module.c:153:5: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/home/guru/Downloads/ieee80211-1.2.18/ieee80211_module.c: In function &#8216;ieee80211_init&#8217;:
/home/guru/Downloads/ieee80211-1.2.18/ieee80211_module.c:268:40: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/guru/Downloads/ieee80211-1.2.18/ieee80211_module.c:268:40: note: each undeclared identifier is reported only once for each function it appears in
/home/guru/Downloads/ieee80211-1.2.18/ieee80211_module.c: In function &#8216;ieee80211_exit&#8217;:
/home/guru/Downloads/ieee80211-1.2.18/ieee80211_module.c:297:31: error: &#8216;proc_net&#8217; undeclared (first use in this function)
{standard input}: Assembler messages:
{standard input}: Warning: can't open .lst: Permission denied
GAS LISTING  			page 1


   1              	 .file "ieee80211_module.c"
   2              	 .text
   3              	.Ltext0:

GAS LISTING  			page 2


DEFINED SYMBOLS
                            *ABS*:0000000000000000 ieee80211_module.c

NO UNDEFINED SYMBOLS
make[2]: *** [/home/guru/Downloads/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/guru/Downloads/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [modules] Error 2

[/b]

If i have to install my ipw3945abg, i have to complete iee80211-1.2.18 first. 

I totally new to this kind of stuffs. So please help me to sort this out. If you need more details, i would be providing it on request. 


Thanks

---

### Post by bkratz on 2012-04-11
I think the first thing I would do is install rfkill

sudo apt-get install rfkill

I believe the driver is iwl3945 and should be resident in the kernel.  look at lsmod (that is LSMOD) in lowercase and see what modules are loaded.

Then post the outputs of

rfkill list all
dmesg | grep iwl


Additional information can be found here

[http://ubuntuforums.org/showthread.php?t=1689100](http://ubuntuforums.org/showthread.php?t=1689100)

---

