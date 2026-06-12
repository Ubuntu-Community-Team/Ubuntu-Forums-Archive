---
title: "Lenovo V570 SD card reader"
date: 2011-07-04
forum: Hardware
---

### Post by dot-borg on 2011-07-04
Hi, my SD card reader isn't working and I'd like to fix that. Unfortunately, I'm not sure which device it is. Here's the output from lspci:
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
```And here's the output from lsusb:
```
Bus 002 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 1c7a:0603 LighTuning Technology Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 5986:0364 Acer, Inc 
Bus 001 Device 003: ID 8087:07d7 Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```I suspect that it might be the Realtek USB device. Anyone have an idea?

---

### Post by jvgeli on 2011-07-08
Have the same issue on a Lenovo G475 with Realtek Multi Card reader running maverick. Anyone figured this out yet pleasE?

---

### Post by Amorget on 2011-07-12
Same SD Card reader, same problem.  This is in a MSI 16F2 whitebook

---

### Post by freechelmi on 2011-07-15
Hi ! 

Same probleme here with a Lenovo B570 , at least it's not 1c7a:0603 which is the fingerprint reader certified by ubuntu : [http://www.ubuntu.com/certification/catalog/make/usb:1C7A](http://www.ubuntu.com/certification/catalog/make/usb:1C7A) .

It seems to be 0bda:0139 then ...

---

### Post by gseward on 2011-07-19
Same SD Card reader, same problem. This also is in a MSI 16F2 whitebook.  Ub 11.04.  I have been unable to identify the card reader.
----------
gil@UbZNb:~$ lsusb
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 047d:1043 Kensington 
Bus 002 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching HubID 0bda:0139 Realtek Semiconductor Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1770:ff00  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
-------------
I think it is the ID 0bda:0139 Realtek Semiconductor Corp..
Any ideas would be greatly appreciated.

---

### Post by freechelmi on 2011-07-19
> **gseward said:**
> 
I think it is the ID 0bda:0139 Realtek Semiconductor Corp..
Any ideas would be greatly appreciated.

It is . RealTek sent me a driver for this Vid/pid but I haven't tested it yet.

It's available here : [http://ubuntuone.com/p/153B/](http://ubuntuone.com/p/153B/)

---

### Post by Amorget on 2011-07-19
> **freechelmi said:**
> It is . RealTek sent me a driver for this Vid/pid but I haven't tested it yet.

It's available here : [http://ubuntuone.com/p/153B/](http://ubuntuone.com/p/153B/)

Works perfectly on the 16F2!

Really simple install, just read the readme

extract to HDD, open terminal and navigate to folder.
```
make
sudo make install
sudo depmod
```


reboot

Thank you so much!

---

### Post by gseward on 2011-07-19
Works perfectly on my MSI 16f2 (16F231-004) with Ubuntu 11.04.  Only hitch is that I had to go root to do make, not just sudo make.

Thanks a whole lot.  Now everything works.

---

### Post by friv_livs on 2011-07-23
realtek driver download worked for me. Thanks.

---

### Post by freechelmi on 2011-07-23
> **friv_livs said:**
> realtek driver download worked for me. Thanks.

Great thanks for the feedback. We still have to roduce a DKMS package then to ease the installation now

---

### Post by Tema1980 on 2011-07-24
> **freechelmi said:**
> It is . RealTek sent me a driver for this Vid/pid but I haven't tested it yet.

It's available here : [http://ubuntuone.com/p/153B/](http://ubuntuone.com/p/153B/)

Can you place it somewhere else? I cant open this page :(

---

### Post by freechelmi on 2011-07-24
Seems like UbuntuOne is not that reliable ! 

I've attached the Tarball

---

### Post by Tema1980 on 2011-07-24
thnx, I'll try it right now

---

### Post by freechelmi on 2011-07-24
> **dot-borg said:**
> Hi, my SD card reader isn't working and I'd like to fix that.

DOt-Borg : Could you change the thread subject to 'Realtek USb Card Reader driver  0bda:0139 ' ?

Would be easier for people to find it

---

### Post by Tema1980 on 2011-07-24
Thanks! It just works!

---

### Post by bph on 2011-07-29
excellent advice, thanks very much, my lenovo b570 card reader now working perfectly

---

### Post by marjeo on 2011-07-29
Solved!
This has solved my problem after 3 months of searching for an answer!
My Card Reader is now working! Ubuntu 11.04 is just perfect! All my hardwares are working and serving me at their best!
Thanks a lot!:D

---

### Post by marjeo on 2011-07-29
This is simply awesome! This worked very well in my Lenovo G460e laptop! Thanks a lot freechelmi. Cheers!

---

### Post by BlaXpirit on 2011-08-24
This worked for me, thanks :)

At first I had a problem: I couldn't write files to my memory card, but the card was just messed up. I formatted it, and then it worked fine.

---

### Post by finomeno on 2011-08-24
> **freechelmi said:**
> It is . RealTek sent me a driver for this Vid/pid but I haven't tested it yet.

It's available here : [http://ubuntuone.com/p/153B/](http://ubuntuone.com/p/153B/)

Thank you so much! A simple compile and my cardreader works (:

That's on a G470 by the way (0bda:0139).

---

### Post by freechelmi on 2011-09-04
> **finomeno said:**
> Thank you so much! A simple compile and my cardreader works (:

That's on a G470 by the way (0bda:0139).

Great ! This realtak driver is currently being added in the kernel Tree, so maybe for 12.04.

---

### Post by abecrab on 2011-09-20
This also works for the Lenovo Z370 for 11.04 Natty.

Thanks very much indeed all of you.

---

### Post by Juraj Cerven on 2011-10-06
Thanks very much - it works also on my Lenovo IdeaPad G575 with Linux Mint 10. :D

---

### Post by www.rzr.online.fr on 2011-10-13
do you use that driver on linux 3 ?


let me link to debian related post :

[http://forums.debian.net/viewtopic.php?f=7&t=67924&p=398309#p398309](http://forums.debian.net/viewtopic.php?f=7&t=67924&p=398309#p398309)

-- 
[http://rzr.online.fr/q/lenovo](http://rzr.online.fr/q/lenovo)

---

### Post by freechelmi on 2011-10-13
> **www.rzr.online.fr said:**
> do you use that driver on linux 3 ?


let me link to debian related post :

[http://forums.debian.net/viewtopic.php?f=7&t=67924&p=398309#p398309](http://forums.debian.net/viewtopic.php?f=7&t=67924&p=398309#p398309)

-- 
[http://rzr.online.fr/q/lenovo](http://rzr.online.fr/q/lenovo)

Hi RZR , good to see you here :-) 

Actually the module is now included in 3.0.0-12 on ubuntu 11.10, so you should see it in Debian as well I guess ?

---

### Post by www.rzr.online.fr on 2011-10-16
hi freechelmi,

Yes I figured it out, now i am busy w/ acpi and wifi

Are you happy w/ Lenovo G570 see ya again online ...

---

### Post by biji on 2011-12-01
The driver does not work for me :(
0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader

---

### Post by acron1 on 2012-03-04
Thank you this worked for me as well Asus X44H and Fedora 16 KDE...

---

### Post by majedaly on 2012-07-13
> **Amorget said:**
> Works perfectly on the 16F2!

Really simple install, just read the readme

extract to HDD, open terminal and navigate to folder.
```
make
sudo make install
sudo depmod
```
reboot

Thank you so much!

Thanks, that worked for me for Lenovo G470, running linux mint 13

---

