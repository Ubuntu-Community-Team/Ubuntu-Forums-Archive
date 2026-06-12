---
title: "how does one setup wireless internet with a pci card in 9.1"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by bjaz on 2009-11-05
hi
i've just done a clean install of ubuntu 9.1 on a japanese sony VAIO VGN FS21B

all is well but i can't get the wireless internet going. it's a PCI adapter. i've looked in system / administration network but don't really understand what i'm supposed to do

previous installs with xubuntu worked out of the box, just entered the network name and wep key, but i'm a little lost here. seems like the wireless adapter isn't recognized.

another unrelated question : once everything goes well one this install, how do i delete the other installs, can I just use GParted and delete the other install partitions ? won't this disturb the Grub and boot process ?

thanks in advance for your help

ben

---

### Post by bjaz on 2009-11-06
i'm getting online with the updated version of xubuntu, where the wireless work, only the touchpad and sound have issues.
but in the new clean ubuntu 9.1 install, sound and touchpad work, yet i can't get the wireless going.

here is the info mentioned as necessary in the wifi thread :

kayo@kayo-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
kayo@kayo-ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kayo@kayo-ubuntu:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:01:4a:60:fa:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:b0106000-b0106fff ioport:2000(size=64)
kayo@kayo-ubuntu:~$ uname -a
Linux kayo-ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
kayo@kayo-ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic
kayo@kayo-ubuntu:~$ 

kayo@kayo-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
kayo@kayo-ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kayo@kayo-ubuntu:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:01:4a:60:fa:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:b0106000-b0106fff ioport:2000(size=64)
kayo@kayo-ubuntu:~$ uname -a
Linux kayo-ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
kayo@kayo-ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic
kayo@kayo-ubuntu:~$

---

### Post by bjaz on 2009-11-06
bump

can onyone help ?
it's a strange situation. wireless works fine in the xubuntu upgrade, but sound and touchpad don't work.
and in the new 9.1 ubuntu install, sound and touchpad work, but i really can't figure out how to get online

b

---

### Post by Maheriano on 2009-11-06
Are you sure? Any of the wireless PCI cards I'm using just plug in and work right away. One time I had to go to System and check for available drivers fro my hardware and it found one for the wireless card. That worked until I upgraded and I didn't need it anymore. Try that.

---

### Post by bjaz on 2009-11-07
when I checked for the drivers it said "no proprietary drivers available".

but maybe it's just a something I have to enable in the settings, yet i can't find it.
the "network" or "connection" sections of system / administration don't have an enable wireless button that I can see.

I added the specs to my wireless connection, but nothing happens.

the adapter works fine under xubuntu, even after the update, but on this new Ubuntu 9.1 intall i really can't get it to work

what checks could i run ?

thanks a lot

ben

---

### Post by bigfuntoe on 2009-11-07
Should as said work out of the box,

Unless I'm being particularly stupid (always possible) I don't see your Wifi device in your lspci output

can you post the output of sudo ifconfig as well please.

W

---

### Post by bjaz on 2009-11-07
yep, w've never had such issues previously and it still works on the xubuntu 9.1 update.

here's the ifconfig, it's my wife's computer hence in french, let me know if this is ok :

                                       [LEFT]eth0      Link encap:Ethernet  HWaddr 00:01:4a:60:fa:c0  [/LEFT]
    [LEFT]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/LEFT]
    [LEFT]          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0[/LEFT]
    [LEFT]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/LEFT]
    [LEFT]          collisions:0 lg file transmission:1000 [/LEFT]
    [LEFT]          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)[/LEFT]
    
    [LEFT]lo        Link encap:Boucle locale  [/LEFT]
    [LEFT]          inet adr:127.0.0.1  Masque:255.0.0.0[/LEFT]
    [LEFT]          adr inet6: ::1/128 Scope:Hôte[/LEFT]
    [LEFT]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/LEFT]
    [LEFT]          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0[/LEFT]
    [LEFT]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/LEFT]
    [LEFT]          collisions:0 lg file transmission:0 [/LEFT]
    [LEFT]          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)[/LEFT]
    
    [LEFT]kayo@kayo-ubuntu:~$ [/LEFT]

---

### Post by bigfuntoe on 2009-11-07
No actually it's not ! 

I'd expect to see entries for 
wlan0
and wmaster0

eth0 is your wired ethernet.

I had a quick google for that machine and couldn't find any hardware details. I'm not sure what the wifi chipset is in place.

---

### Post by bjaz on 2009-11-07
no there's no wifi on this machine.

it's a pci adapter card, which works fine for windows XP and Xubuntu. I'll post the if config of the xubuntu version, where wireless worked 3out of the box"

it works fine under xubuntu, on the same machine, and still does after the update to 9.1 --- so there's no issue with the machine or adapter - but other issues which made me want to migrate to ubuntu, and get rid of the xubuntu partition. hence a new clean install, side by side. yet there's no wirless internet....

I did a new install of ubuntu, standard i386, parallel as we would like to use this from now, and get rid of xubuntu (which also has new issues since the upgrade, such as no sound or touchpad after the update)

and here, on ubuntu 9.1, the AMTEL pci adapter card doesn't work out of the box, i have no internet / can't get the wireless working.

hence my thread calling for help with getting the wirless working on Ubuntu 9.1. hope this isn't too confusing.

ath the worst I could focus on fixing things in the xubuntu install which has a working internet, but there are many issues which make me lean in favour of a clean, new ubuntu install like the one we now have, where we just can't get the internet working.

I'mm post the ifconfig of the working xubuntu install, but please understand that though internet works onf this one, this is the one we're trying to get rid of due to other problems (japanese anthy gone wild, sound, touchpad, disk read and write permissions)

what I posted are the results of the ifconfig of this clean ubuntu install.

but we've been using xubuntu on the machine for a while, with no wireless issues, though there have been others, and more since the upgrade, hence my desire for a clean start on an Ubuntu install. But it doesn't work "out of the box" like ot does on xubuntu, for a reason.

---

### Post by bjaz on 2009-11-07
ok, this is the ifconfig from the xubuntu version i'm currently writing on, same machine, wireless works fine.

kayo@kayogoro:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:4a:60:fa:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:06:f4:04:8c:5b  
          inet adr:192.168.1.21  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::206:f4ff:fe04:8c5b/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:998 erreurs:73 :0 overruns:0 frame:0
          TX packets:672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1107233 (1.1 MB) Octets transmis:149687 (149.6 KB)
          Interruption:3 Adresse de base:0x2040 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

kayo@kayogoro:~$ 

-------------------

but this is also the version that i would prefer to get rid of, settling for plain ubuntu instead.

can anyone help me get the wireless working on ubuntu, like it does on this machine's xubuntu install ?

thanks a bunch

ben

---

### Post by bjaz on 2009-11-08
I really hope someone can see through this if it will be possible to get the wireless working on ubuntu like it works on xubuntu, or should i just discard the install for now and downgrade the xubuntu install with working internet ?

thanks

b

---

### Post by bjaz on 2009-11-09
I was thinking, since I have a working wireless on the xubuntu install, couldn't I copy the config file somewhere, then replace the existing one in ubuntu ?
i really don't know where it owuld be or if it is very different ?

thanks

ben

---

### Post by bjaz on 2009-11-11
I forgot to add that I can go online with an ethernet cable.

the wifi adapter worked fined in previous versions, what could be wrong ?

can anyone help out ? I do realize no one is "entitled to support", but i'm really stuck here

thanks

ben

---

### Post by gordintoronto on 2009-11-11
> **bjaz said:**
> no there's no wifi on this machine.

it's a pci adapter card, which works fine for windows XP and Xubuntu. I'll post the if config of the xubuntu version, where wireless worked 3out of the box"
...
and here, on ubuntu 9.1, the AMTEL pci adapter card doesn't work out of the box, i have no internet / can't get the wireless working.


For 99.9% of the world, wireless=wifi, which is why no one has been able to help you.  I assume this PCI card was supplied by a cell phone company?  If you gave an exact description of it (brand and model) it might help, or perhaps you could do a google search using the model number.

In Ubuntu, it's as if the card has been removed from the computer.  Did you post output from lspci?

---

### Post by bjaz on 2009-11-11
yes, it's an old WIFI AMTEL PCI adapter card which worked out of the box in xubuntu jaunty, and still does after the karmic update, but simply refuses to in a new clean ubuntu 9.1 intall


the lspci outpost is posted on the previous page of this thread.

the wifi card is a *ATMEL INVENTEL* Wireless Network Adapter AT76C502A. FCC ID:*KFY*-[I]WA1113
[/I]at76c502ar_e 

worked out of the box in the xubuntu and still does after the karmic update, but refuses to work in standard ubuntu which i know plan on using for this machine

thanks in advance for your help

---

### Post by bjaz on 2009-11-16
summed it up with required specs here

[http://ubuntuforums.org/showthread.php?t=1328098](http://ubuntuforums.org/showthread.php?t=1328098)

---

### Post by bjaz on 2009-11-18
is there really nothing else to be done, and any chance that this might be looked at in following updates ?

thanks 

ben

---

### Post by gordintoronto on 2009-11-19
I understand you have changed back to Xubuntu 9.04.  Does the PCMCIA card show up when you run lspci?  (I would not expect it to.)

I went to the Ubuntu Team Wiki, which is available from the Ubuntu home page, and looked up pcmcia.  It appears there is an lspcmcia command.  If you boot from the 9.10 live CD and enter that command, does the wifi card show up?  In 9.04 Xubuntu, what does lspcmcia show?

---

### Post by bjaz on 2009-11-21
hi and thanks.
everything works fine under Xubuntu 9.04, the PCMIA is recognized and works out of the box.

the problem with the pcmcia adapter is only in ubuntu 9.10

i'm on xubuntu 9.04 now

kayo@kayo-Xubuntu:~$ lspcmcia
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:06:03.0)
Socket 0 Device 0:    [atmel_cs]        (bus ID: 0.0)
kayo@kayo-Xubuntu:~$

it connects to all networks fine. I just wish i could get the PCMCIA adapter to work on unbuntu 9.10--- isn't it strange that it should work out of the box in 9.04 and not in 9.10, on the same machine ?

---

### Post by bjaz on 2009-11-22
and do people think the ndis wrapper with the windows driver might actualy work ?

thanks

b

---

### Post by gordintoronto on 2009-11-22
> **bjaz said:**
> and do people think the ndis wrapper with the windows driver might actualy work ?

thanks

b

Maybe, if the card shows up in lspcmcia

---

### Post by bjaz on 2009-11-23
this is the windows driver

[http://download.porciello.com/inventel/dwb200/Pilotes_Carte_PCMCIA_WiFi_ATMEL.zip](http://download.porciello.com/inventel/dwb200/Pilotes_Carte_PCMCIA_WiFi_ATMEL.zip)


all the details to the issue, including one big help, are in this thread which is much clearer

[http://ubuntuforums.org/showthread.php?t=1328098](http://ubuntuforums.org/showthread.php?t=1328098)



kayo@kayo-oppo:~$ lspcmcia
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:06:03.0)
Socket 0 Device 0:    [pata_pcmcia]        (bus ID: 0.0)

---

