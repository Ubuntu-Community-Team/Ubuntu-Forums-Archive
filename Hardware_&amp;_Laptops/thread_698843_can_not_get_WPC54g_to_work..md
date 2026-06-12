---
title: "can not get WPC54g to work."
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by paries on 2008-02-16
i have followed many many threads, but i am getting knowwhere

i have compiled ndiswrapper successfully

but when i run 
# ndiswrapper -i lsbcmnds.inf
installing lsbcmnds ...

I get no hardware info

modeprob works

#lshw -C network:

*-network UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=0

#lspci -v
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Linksys WPC54G-EU version 3 [Wireless-G Notebook Adapter]
        Flags: fast devsel, IRQ 10
        Memory at 28000000 (32-bit, non-prefetchable) [disabled] [size=8K]

But when i do
#  iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

ifconfig does not see it

Any ideas or directions?????

Thanks

---

### Post by SixedUp on 2008-02-17
> **paries said:**
> 
i have compiled ndiswrapper successfully

You shouldn't need to compile ndiswrapper ... on Gutsy you should be able to simply install it using:
```

sudo apt-get install ndiswrapper-utils-1.9

```

> 
but when i run 
# ndiswrapper -i lsbcmnds.inf
installing lsbcmnds ...

I get no hardware info

modeprob works

#lshw -C network:

*-network UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=0


The hardware is not being claimed by a driver. Could be ndiswrapper isn't installed properly, so make sure you've installed ndiswrapper as suggested above. Then make sure that you really do have the right Windows driver for your card, and that it's supported by ndiswrapper. Check out [the ndiswrapper wiki website]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/") for more information. if that doesn't get you going then repost here.

---

### Post by paries on 2008-02-18
Richard 
thanks for  your help.

I am not getting a little closer.... I think...

now when i do 
#lshw -C network
*-network UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=0

but i still get this return
#  iwlist wlan0 scan
wlan0     Interface doesn't support scanning.


Thanks
Randy

---

### Post by Subliminal Aura on 2008-02-18
Make sure you have the correct drivers for your WPC54G there are plenty of different versions for the same model on the linksys site....

Mine is a WPC54G**v5**

Here's my conf...

root@vaio:/etc/ndiswrapper/lsmvnds# ls -al
total 292
drwxr-xr-x 2 root root   4096 2006-11-03 00:08 .
drwxr-xr-x 3 root root   4096 2006-11-03 00:08 ..
-rw-r--r-- 1 root root    646 2006-11-03 00:08 oopsmymac:0040.5.conf
lrwxrwxrwx 1 root root     51 2006-11-03 00:08 oopsmymac.conf -> /etc/ndiswrapper/lsmvnds/11AB:1FAA:1737:0040.5.conf
-rw-r--r-- 1 root root  12856 2006-11-03 00:08 lsmvnds.inf
-rw-r--r-- 1 root root 265344 2006-11-03 00:08 mrv8335xp.sys


grep ndis /var/log/messages

Feb 17 10:06:28 vaio kernel: [17179602.252000] ndiswrapper: using irq 9
Feb 17 22:39:31 vaio kernel: [17179602.180000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
Feb 17 22:39:31 vaio kernel: [17179602.324000] ndiswrapper: driver lsmvnds (Linksys,10/13/2004,3.1.0.36 ) loaded
Feb 17 22:39:31 vaio kernel: [17179602.372000] ndiswrapper: using irq 9
Feb 18 10:17:37 vaio kernel: [17179601.836000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
Feb 18 14:56:23 vaio kernel: [17179602.260000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
Feb 18 15:22:25 vaio kernel: [17179602.108000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)

---

### Post by paries on 2008-02-18
thanks for all the help.
Got it to work

i went to the linksys site and download the 
WPC54G_Setup_Wizard_3.1
(my card is V3)

i unzipped it went to 
/home/WPC54G_3.1/WPC54G_Setup_Wizard_3.1/Driver/NT

removed the old one
# ndiswrapper -r lsbcmnds

# ndiswrapper -i LSBCMNDS.inf
installing lsbcmnds ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2

ndiswrapper -l
lsbcmnds : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)


Thanks for all the help

---

