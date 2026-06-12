---
title: "freezing when doing anything...."
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by KiaZiShiru on 2009-11-08
The installation itself seemed to work just fine, only now I&#472;e got a couple of problems... both on my ubuntu and on my vista since I dual booted the two of them. This is my first dual boot so I&#7743; not sure what problems people usually have doing it.

first on my ubuntu, I installed 9.10.
- Nvidia doesn't work and when I try to install it it freezes.
- I put my language on dutch but now everytime I try to change my desktopimage it wants to install the right stuff for dutch and once again... freezes... 
- I tried changing it in the language settings but that wouldn load, it loads some screen and shutsdown again....
- it also randomly froze a couple of times when I was searching on the net, it hasn't done that again so far.....
Right now I'm too afraid to even try to install anything on this laptop because I don't want it too freeze again.  

EDIT tried installing flash and froze when youtube tried to direct me to the adobe website...

Vista is being a pain in the *** too....
- IE keeps freezing... constantly, so I&#7743; not able to run anything important on it...
- some small programs keep giving me errors but they don particularly matter (the windows sidebar and some small program I run on it for fun)

I have an ASUS, it has a Nvidia GEFORCE GT 220M (1gb) card in it and 4gb dualcore RAM. It has 4 partitions now, 2 vista ones, 1 ubuntu and 1 where both ubuntu and vista can read from.

Who can help me cause I really like linux and was tired of installing everything manually like I usually do with Debian, but right now I almost feel like doing that...

help?

---

### Post by earthpigg on 2009-11-08
first, please ensure you have a solid backup of all your vital data. for your own good, please do this immediately. vital data should not be stored on an unstable system.

moving on...

the quickest thing to test for is CPU overheating. we will test that first, just because it is so quick and easy to test for and/or rule out as the cause.

install lm-sensors:
sudo apt-get install lm-sensors
configure it:
sudo sensors-detect
run it:
sensors

keep an eye on the CPU temp every 5-10 minutes as you use the computer. see if it spikes before your computer freezes. in any case, let us know what your CPU's temperature range is. ie: "it sits idle at 25C, and gets up to 40C when i watch youtube." or whatever the case may be for you.


if this is a true dual boot:

assuming windows boots at all (which it does, in your case), nothing pertaining to Ubuntu would affect Windows in any way at all.

since similar problems are happening on two completely different operating systems on the same hardware, that would indicate ***hardware*** as the problem. as in, some piece of hardware is failing. :(

hard drives and RAM are the two most common things to fail on computer.

hard drive - use [badblocks]("http://en.wikipedia.org/wiki/Badblocks") for your linux partition and windows scandisk for your windows partition. select the 'test for physical errors' option in scandisk.

RAM - [memtest86+]("http://www.memtest86.com/"). it takes many hours to test, but does a very thurough job. start it before you go to bed, so it will be done when you wake up. or before you go to work, so it will be done when you come home.


if this is a WUBI install (not true dual boot):

use scandisk in MS windows as above, no need for badblocks (a problem with the windows filesystem will also make Ubuntu usntable, on a WUBI install).

if that doesn't find any problems, try memtest86+.



if none of that returns anything, the next step will be s.m.a.r.t. testing, a bridge we can cross when we get to it.



edit: can you run windows long enough to disable any/all desktop effects, such as that "windows aero" stuff? and, set desktop effects to 'none' in ubuntu's system -> preferences -> appearance interface. if that suddenly fixes everything in either case, the problem is ***probably*** video card hardware failure.


edit2: the quickest/easiest things to test are the CPU temp at the top of the post, and the video card stuff in my first edit. may as well do that first, since its quickest and easiest.

---

### Post by KiaZiShiru on 2009-11-08
luckally I don't have much vital data on it anyway, since its mostly schoolwork and a couple of games.... 

the temp is steady around 52/ 53 C.    

***********edit *********
these are the regular temps I get.
Adapter: Virtual device
temp1:       +53.0°C  (crit = +97.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +39.0°C  (high = +85.0°C, crit = +85.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +39.0°C  (high = +85.0°C, crit = +85.0°C)  
****************************

okay, it just froze so I'll be doing the vista checkup now, and no temp rising before it froze. Also not sure what it was that made it freeze in the first place.    

okay, vista runs perfect now, no freezing, no crazy stuff, I'm even able to open and run a couple of games and CPU never gets above 30%.... desktop addons function fine too....  I didn't change anything from the last 3 times I tried to work with it (apart from just putting it away for an hour because I was annoyed)...     

now I'm gonna see if ubuntu is gonna work oke for me this time around...

I think the prob might be the driver software for my videocard... any way to fix that?

---

### Post by KiaZiShiru on 2009-11-08
okay, somehow I&#7743; also not able to log on as root (autentication failed) and my sounds isn't working. Maybe I should just load 9.04 on it and try from there... 

also... no VLC? what the? It won't show in my download list. 

I've made a couple of changes (de-installed all of the games...) and it hasn't frozen up yet. so now I&#7743; off to bed and I&#314;l see how everything turns out in the morning.

---

### Post by michaelzap on 2009-11-08
You might try installing the latest Release Candidate for the kernel (2.6.32-rc6) as found here:
[http://ubuntuforums.org/showpost.php?p=8263419&postcount=135](http://ubuntuforums.org/showpost.php?p=8263419&postcount=135)

That fixed constant freezing and crashing for me.

---

### Post by KiaZiShiru on 2009-11-09
I'm not sure how that works... how to do that.  and ubuntu somehow crashed on me when I just went to desktop this morning.

---

### Post by michaelzap on 2009-11-09
> **KiaZiShiru said:**
> I'm not sure how that works... how to do that.  and ubuntu somehow crashed on me when I just went to desktop this morning.

Just download three .deb files from the latest (RC6) folder: The headers and kernel file for your architecture (i386 or amd64) and the "all" headers file (you don't need the "source" file). Then double-click on them to install (if you get dependency errors that just means you need to install them in the right order). After that reboot and choose the new kernel from the grub menu.

If it doesn't work better for you, just reboot again and choose the older kernel. You can remove it if you like using Synaptic, but it doesn't hurt anything to leave it there.

---

### Post by KiaZiShiru on 2009-11-09
okay, thanks, I'll try that.

---

### Post by KiaZiShiru on 2009-11-09
thnx, this worked ^^ now I&#7743; trying to get some other programs running...

---

### Post by michaelzap on 2009-11-09
> **KiaZiShiru said:**
> thnx, this worked ^^ now I&#7743; trying to get some other programs running...

Excellent!

---

### Post by oxTux on 2009-11-09
My computer (ubuntu 8.10 kernel 2.6.27-14)  also freezes, and as it's said before the core temp is alright.
the point is when the processor is idle or "almost" idle it freezes. I guess if it's a hardware driver problem

my computer and its drivers
H/W path           Device      Class       Description
======================================================
                               system      Aspire 5610
/0                             bus         Grapevine
/0/0                           memory      101KiB BIOS
/0/4                           processor   Genuine Intel(R) CPU           T2250  @ 1.73GHz
/0/4/5                         memory      2MiB L2 cache
/0/4/1.1                       processor   Logical CPU
/0/4/1.2                       processor   Logical CPU
/0/a                           memory      1536MiB System Memory
/0/a/0                         memory      1GiB SODIMM Synchronous
/0/a/1                         memory      512MiB SODIMM Synchronous
/0/1                           processor   
/0/1/1.1                       processor   Logical CPU
/0/1/1.2                       processor   Logical CPU
/0/100                         bridge      Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
/0/100/2                       display     Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
/0/100/2.1                     display     Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
/0/100/1b                      multimedia  82801G (ICH7 Family) High Definition Audio Controller
/0/100/1c                      bridge      82801G (ICH7 Family) PCI Express Port 1
/0/100/1c.1                    bridge      82801G (ICH7 Family) PCI Express Port 2
/0/100/1c.2                    bridge      82801G (ICH7 Family) PCI Express Port 3
/0/100/1c.3                    bridge      82801G (ICH7 Family) PCI Express Port 4
/0/100/1c.3/0      wmaster0    network     PRO/Wireless 3945ABG [Golan] Network Connection
/0/100/1d                      bus         82801G (ICH7 Family) USB UHCI Controller #1
/0/100/1d.1                    bus         82801G (ICH7 Family) USB UHCI Controller #2
/0/100/1d.2                    bus         82801G (ICH7 Family) USB UHCI Controller #3
/0/100/1d.3                    bus         82801G (ICH7 Family) USB UHCI Controller #4
/0/100/1d.7                    bus         82801G (ICH7 Family) USB2 EHCI Controller
/0/100/1e                      bridge      82801 Mobile PCI Bridge
/0/100/1e/1        eth0        network     BCM4401-B0 100Base-TX
/0/100/1e/4                    bridge      CB-712/4 Cardbus Controller
/0/100/1e/4.1                  memory      FLASH memory
/0/100/1e/4.2                  system      ENE PCI Secure Digital Card Reader Controller
/0/100/1e/4.3                  memory      FLASH memory
/0/100/1e/4.4                  memory      FLASH memory
/0/100/1f                      bridge      82801GBM (ICH7-M) LPC Interface Bridge
/0/100/1f.2        scsi0       storage     82801GBM/GHM (ICH7 Family) SATA IDE Controller
/0/100/1f.2/0      /dev/sda    disk        120GB Hitachi HTS54161
/0/100/1f.2/0/1    /dev/sda1   volume      6997MiB Windows NTFS volume
/0/100/1f.2/0/2    /dev/sda2   volume      52GiB Windows NTFS volume
/0/100/1f.2/0/3    /dev/sda3   volume      2863MiB Linux swap volume
/0/100/1f.2/0/4    /dev/sda4   volume      49GiB EXT3 volume
/0/100/1f.2/0/4/5  /dev/sda5   volume      38GiB Linux filesystem partition
/0/100/1f.2/0/4/6  /dev/sda6   volume      11GiB Linux filesystem partition
/0/100/1f.2/1      /dev/cdrom  disk        DVD-RW DVR-K17RS
/0/100/1f.3                    bus         82801G (ICH7 Family) SMBus Controller
/1                 pan0        network     Ethernet interface 

if anyone have any  idea of the problem please guide me
thanks very very much!!

---

