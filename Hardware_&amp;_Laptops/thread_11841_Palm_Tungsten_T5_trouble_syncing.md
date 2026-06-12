---
title: "Palm Tungsten T5 trouble syncing"
date: 2005-01-19
forum: Hardware &amp; Laptops
---

### Post by Yoda_Oz on 2005-01-19
i have a palmone tungsten t5 running Ubuntu linux (debian-based).

im trying to use gnome pilot (i've also tried to use coldplug too...) and i try to hotsync and nothing happens. it just sits there saying something like its waiting to send info to my handheld. i havent succeeded in connecting as yet but at least my computer is seeing the device!
here are some outputs:

/proc/bus/usb/devices

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 53 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=0830 ProdID=0061 Rev= 1.00
S:  Manufacturer=palmOne, Inc.
S:  Product=palmOne Handheld
S:  SerialNumber=504E35424D41413456375852
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=00 Prot=00 Driver=visor
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=86(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=07(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

lsusb

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 053: ID 0830:0061 Palm, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 016: ID 046d:c016 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

/var/log/messages

Jan 20 23:03:11 localhost kernel: usb 2-1: new full speed USB device using address 53
Jan 20 23:03:11 localhost kernel: visor 2-1:1.0: Handspring Visor / Palm OS converter detected
Jan 20 23:03:11 localhost kernel: usb 2-1: Handspring Visor / Palm OS converter now attached to ttyUSB2
Jan 20 23:03:11 localhost kernel: usb 2-1: Handspring Visor / Palm OS converter now attached to ttyUSB3
Jan 20 23:03:11 localhost usb.agent[15466]:      visor: already loaded

Have i left out anything???

Cheers for all your help!!!

---

### Post by steffen on 2005-01-20
Based on your many attempts, I would say you have probably tried this, but I went through a lot before changing /dev/pilot to /dev/ttyUSB0 - suddenly it detected...

---

### Post by h4d on 2005-01-27
I'm having the same problem with the same Tungstein|T5. Please post if you got it working!
Thanks!

---

### Post by h4d on 2005-01-27
I got it working with JPilot, only it works with root and not with a regular user, so if you run sudo jpilot and configure it should work for you. It's actually pretty anoying not to be able to sync as a normal user, anyone know why?

---

### Post by steffen on 2005-01-27
maybe you could try sudo chmod 777 /dev/ttyUSB0 and sudo chmod 777 /dev/pilot and sudo chmod 777 /dev/ttyUSB1

---

### Post by h4d on 2005-01-27
[QUOTE=steffen]maybe you could try sudo chmod 777 /dev/ttyUSB0 and sudo chmod 777 /dev/pilot and sudo chmod 777 /dev/ttyUSB1[/QUOTE]
 Just tried that, unsuccesfully :(

---

### Post by Viro on 2005-02-01
[QUOTE=h4d]Just tried that, unsuccesfully :([/QUOTE]
 Has any of you tried looking at the Wiki?  [http://www.ubuntulinux.org/wiki/PalmZire31HOWTO](http://www.ubuntulinux.org/wiki/PalmZire31HOWTO)

It's kinda new, so try it and see if it solves your problems.

---

### Post by h4d on 2005-02-06
[QUOTE=Viro]Has any of you tried looking at the Wiki?  [http://www.ubuntulinux.org/wiki/PalmZire31HOWTO](http://www.ubuntulinux.org/wiki/PalmZire31HOWTO)

It's kinda new, so try it and see if it solves your problems.[/QUOTE]
 Just tried it too, nothing!

---

### Post by robenroute on 2005-10-19
I've posted a possible solution to the sync problem:

[http://www.ubuntuforums.org/showthread.php?t=78918](http://www.ubuntuforums.org/showthread.php?t=78918)

---

