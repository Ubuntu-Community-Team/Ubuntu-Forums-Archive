---
title: "Sata controller card"
date: 2009-02-16
forum: Hardware
---

### Post by sinkje on 2009-02-16
Hello
I'm trying to get a PCI sata card (syba sd-sata150r) to work with ubuntu server for the purposes of a file server. I cannot find a procedure anywhere on the net to get this card to work. It shows up upon boot before GRUB and reads the hard drive. once ubuntu server boots the drive isn't there. Any suggestions on how to proceed?

---

### Post by sinkje on 2009-02-17
output of df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              18G  716M   17G   5% /
tmpfs                 346M     0  346M   0% /lib/init/rw
varrun                346M  248K  346M   1% /var/run
varlock               346M     0  346M   0% /var/lock
udev                  346M  2.7M  344M   1% /dev
tmpfs                 346M     0  346M   0% /dev/shm
lincoln@lincoln:~$ cd /dev/ata1
-bash: cd: /dev/ata1: No such file or directory

output of lspci

lincoln@lincoln:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

---

### Post by autocrosser on 2009-02-17
Google--Linux search turned up several pages of references to your card--Syba Web indicates that it is for Windows & Mac only--they show (link): [http://www.syba.com/Product/Info/Id/330](http://www.syba.com/Product/Info/Id/330)  as being Linux supported....

---

### Post by sinkje on 2009-02-17
Other people who have bought it from newegg are using it with Linux, they are using different distros though
For some reason i cannot properly link to those pages here.

If there is a Linux driver for this thing how would i go about installing it?
I'm just now getting into Linux and I'm noticing the driver procedure is different.

If i have to i will get another card, I'm just using this one because it's leftover from a win box.

---

### Post by autocrosser on 2009-02-17
Well--I'm not a real good answerer here--I look at the specs for your card & the link I sent you & there seems to be a bit of difference as to how well the card is "supported" in Linux--The final description in the 150 card indicates that it is supported, but it tends to look like "just" supported--

If you are new---Welcome & I know it's quite a bit harder to make some things work--I really look for things that "really" talk about Linux support before I get them--We in the Linux community tend to vote with our dollars.....And I have seen support increase 4x over the last 10 years or so...So just hang it there & bookmark Google Linux---it's better that just using Google.....

---

### Post by sinkje on 2009-02-17
I have found drivers for this card, can anyone instruct me on how to use these things? There are two files that claim to be drivers they are called siimage.c and siimage.h

---

### Post by sinkje on 2009-02-17
Autocrosser, thank you for the welcome. I found those drivers thanks to you referring me to google linux. Much appriciated

---

### Post by Snypez on 2009-03-24
if someone could clarify what exactly solved this problem and wtf google linux is i would be grateful. i am at the same spot with the siimage.c file trying to install a sata controller for mythbuntu. i tried gcc but got a ton of errors. any help would be much appreciated.

---

### Post by autocrosser on 2009-03-24
Google Linux is:  [http://www.google.com/linux](http://www.google.com/linux)  which "biases" search results towards linux-centric answers---nicer than the generic google search that will put Windows & Mac hits higher on the results.

---

