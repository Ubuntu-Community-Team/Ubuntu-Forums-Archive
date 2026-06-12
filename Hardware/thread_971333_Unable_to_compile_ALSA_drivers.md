---
title: "Unable to compile ALSA drivers"
date: 2008-11-04
forum: Hardware
---

### Post by JustTCO on 2008-11-04
Hi, a some time ago i change my kernel from 8.04-2.6.24-1-generic to 8.04-2.6.24-1-i386 and my sound card became no sound at all, but it was detected

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
01:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
01:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
01:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
01:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
03:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)

```
I search and i find this post that save my day.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Now i update my ubuntu distro from 8.04 to 8.10 and like i expected my sound card is again no sound. I recall the post and try the code again, but an error apear when i did the command:
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)

```
make -C /usr/src/linux-headers-2.6.25-2-386 SUBDIRS=/home/tcoupload/Desktop/NetSoftware/ALSA_downloads/alsa-driver-1.0.18rc3  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.25-2-386'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.25-2-386'
make: *** [compile] Error 2
```

So i go check if the file isn't real there and i found a link that point to himself!

```
/usr/src/linux-headers-2.6.25-2-386$ ls -l Makefile 
lrwxrwxrwx 1 root root 34 2008-11-05 01:44 Makefile -> ../linux-headers-2.6.25-2/Makefile

```

Where is the file?

Is there someone that can help to hear again? thanks :grin: :grin:

---

### Post by tereensio on 2008-11-06
> **JustTCO said:**
> Hi, a some time ago i change my kernel from 8.04-2.6.24-1-generic to 8.04-2.6.24-1-i386 and my sound card became no sound at all, but it was detected

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
01:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
01:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
01:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
01:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
03:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)

```
I search and i find this post that save my day.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Now i update my ubuntu distro from 8.04 to 8.10 and like i expected my sound card is again no sound. I recall the post and try the code again, but an error apear when i did the command:
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)

```
make -C /usr/src/linux-headers-2.6.25-2-386 SUBDIRS=/home/tcoupload/Desktop/NetSoftware/ALSA_downloads/alsa-driver-1.0.18rc3  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.25-2-386'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.25-2-386'
make: *** [compile] Error 2
```

So i go check if the file isn't real there and i found a link that point to himself!

```
/usr/src/linux-headers-2.6.25-2-386$ ls -l Makefile 
lrwxrwxrwx 1 root root 34 2008-11-05 01:44 Makefile -> ../linux-headers-2.6.25-2/Makefile

```

Where is the file?

Is there someone that can help to hear again? thanks :grin: :grin:


I have the same problem:

[...]
&#9474; CPP="gcc -E" CC="gcc" modules                                              &#9618;
 &#9474; make[3]: Entering directory `/usr/src/linux-headers-2.6.25-2-386'          &#9618;
 &#9474; make[3]: Makefile: No such file or directory                               &#9618;
 &#9474; make[3]: *** No rule to make target `Makefile'.  Stop.                     &#9618;
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.25-2-386'           &#9618;
 &#9474; make[2]: *** [compile] Error 2                                             &#9618;
 &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9618;
 &#9474; make[1]: *** [build-stamp] Error 2                                         &#9618;
 &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                   
 &#9474; make: *** [kdist_image] Error 2

---

### Post by Yellow Pasque on 2008-11-06
It appears you don't have the headers for your kernel. You're probably also missing some other packages. I suggest this script: [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

---

