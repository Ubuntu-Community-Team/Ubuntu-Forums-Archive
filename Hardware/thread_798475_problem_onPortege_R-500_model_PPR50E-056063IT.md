---
title: "problem onPortege R-500 model PPR50E-056063IT"
date: 2008-05-18
forum: Hardware
---

### Post by cool2010 on 2008-05-18
I've a sticky problem on this R500 portege, it's a fantastic laptop but when I make lspci, lsusb, lshw with many option I can't fine UMTS modem, I read somewhere that it should be Novatel MSM6275 (or qualcomm).
Second strange thing is that I can't find bluetooth adaptor too.
Just last problem that I've find, when I try to suspend after 2/3 second of suspend state system goes up again.
I'm running kubuntu 8.04 fresh installation.

The other things works, the battery life it's no so long as toshiba declare, because after 4 hours of use it's empty.

I think that it's all.


I hope that someone can help me.

Bye bye

---

### Post by esplinter on 2008-10-13
same problem here,

I have just installed kubuntu x86_64 on portege r500 but I cant turn on the umts/3g modem.

On Windows I use Fn+F8 to activate it. When I use that key combination a new light starts blinking next to the wireless lighth, meaming 3g/umts is turned on but I can´t do this on linux.

I can´t activate it so even lspci can´t find the umts modem.

I tried an option on the bios saying "Device Config: All Devices /  Setup by OS" (tried first option, all devices) but I still cant find the umts modem under linux.

I also downloaded the toshet utility  [[http://www.schwieters.org/toshset/]](http://www.schwieters.org/toshset/]) but didn´t find any option related to 3g/umts modems.

¿any clue about how to activate it??

many thanks in advance.

---

### Post by esplinter on 2008-10-24
hi

finally I have upgrade to kubuntu 8.10 (intrepid) which is still a release candidate (kernel 2.6.27) and set on bios "Device Config: All Devices" and my 3g/umts modem is recognized.


root@leonardo:~$ lsusb
Bus 005 Device 004: ID 0930:0c05 Toshiba Corp.
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0930:1302 Toshiba Corp. Wireless Broadband (3G HSDPA) SM-Bus Minicard Status Port
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by tarique on 2009-02-08
esplinter,

Out of interest, my modem also shows in the list as above (I also have an R500), however I am not really sure how to switch the antenna on so it can see the 3G network. The modem is there, but neither network manager or umtsmon can recognize that it is working. However in Windows it works perfectly.

Appreciate your help. Thanks.

---

### Post by esplinter on 2009-05-05
Hi,

when I posted this I had no sim card to test so I tought it was working. Now I have a working sim and I have the same problem. 

The modem works ok in windows, in linux I can see it en /dev/ttyUSB0 but neither network manager or umtsmon recognize it so in linux I can´t connect using the internal novatel 3g modem.

---

### Post by mfa on 2009-05-13
Hi,

i also have this problem. I know it's not much of a comfort but a bug report has been filed concerning this problem.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/310152](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/310152)

The problem is present in Jaunty, so we'll just have to wait and see if this hardware will someday be supported in ubuntu or kubuntu.

---

### Post by darioriso on 2010-03-04
SOLUTION:

[http://ubuntuforums.org/archive/index.php/t-1221077.html](http://ubuntuforums.org/archive/index.php/t-1221077.html)

---

### Post by h4141 on 2010-12-07
There are [drivers]("http://driverswin.com/portage-r500-ppr50e-windows-xp-driver-download/") for XP. might be set up with wine.  at least I know linux. drive a little bit problematic to find

---

