---
title: "Kubuntu has stopped reading my 8 gig Kingston DataTraveler"
date: 2015-12-07
forum: Hardware
---

### Post by Sephilin on 2015-12-07
My 8 gig Kingston worked just fine until November; as a result, Dolphin refused to read it anymore. Btw, are there any commands that I should post to help solve this problem?

---

### Post by Crafty Kisses on 2015-12-07
What is the output of the following 

```

lsusb 
lspci

```

---

### Post by coldraven on 2015-12-08
You could try using mkusb to wipe the first megabyte. It worked for me. (all data on the stick will be lost) See under the wipe menu here:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by mastablasta on 2015-12-09
it could also be that the drive is corrupted. it died on me 4 months into use without warning. running a USB flash disk check revealed write errors on drive.

---

### Post by Sephilin on 2015-12-09
lsusb shows:

```

Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 147a:e017 Formosa Industrial Computing, Inc. eHome Infrared Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0db0:a97a Micro Star International Bluetooth EDR Device
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

and lspci shows: 

```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB600 IDE
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV630/M76 [Mobility Radeon HD 2600]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV630 HDMI Audio [Radeon HD 2600 Series]
02:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 01)
06:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
06:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
06:04.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
06:04.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

---

### Post by mastablasta on 2015-12-10
you need to use something like F3: [http://oss.digirati.com.br/f3/](http://oss.digirati.com.br/f3/)

or maybe if oyu have a windows PC USB Flash Drive Tester does a good job: [https://www.vconsole.com/download](https://www.vconsole.com/download)

there could be some damaged parts of flash drive or it may simply be failing.

---

### Post by sudodus on 2015-12-10
Please run the following commands while the Kingston pendrive is connected

```
sudo parted -ls
sudo lsblk -fm
```

and post the result within [noparse]```
tags
```[/noparse]

These commands can show if the pendrive is recognized as a mass storage device, /dev/sdx, where x is the drive letter (a or b or c ...). If it is recognized as a mass storage device, the pendrive might be possible to mount manually, or at least its partition table or file system should be possible to repair. If not it is probably damaged beyond repair. See this link: [Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

---

### Post by Sephilin on 2015-12-10
I'll post more results tonight. I tried to install mksub via Konsole and it says that the package is not found. Also googled for a tar file of mkusb and I can't find it.

---

### Post by sudodus on 2015-12-10
The link was there in *coldraven*'s post. Use a PPA

```
sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```


See this link for more details: [mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by Sephilin on 2015-12-10
Here goes the results as promised:

 ```
~$ sudo parted -ls
Model: ATA Hitachi HTS54251 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   63.1GB  63.0GB  primary   ntfs
 3      63.1GB  160GB   96.9GB  extended
 5      63.1GB  158GB   94.7GB  logical   ext4
 6      158GB   160GB   2144MB  logical   linux-swap(v1)

```

```

~$ sudo lsblk -fm
NAME   FSTYPE LABEL           MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                      sda    149.1G root  disk  brw-rw----
&#9500;&#9472;sda1 ntfs   System Reserved            &#9500;&#9472;sda1   100M root  disk  brw-rw----
&#9500;&#9472;sda2 ntfs                              &#9500;&#9472;sda2  58.7G root  disk  brw-rw----
&#9500;&#9472;sda3                                   &#9500;&#9472;sda3     1K root  disk  brw-rw----
&#9500;&#9472;sda5 ext4                   /          &#9500;&#9472;sda5  88.2G root  disk  brw-rw----
&#9492;&#9472;sda6 swap                   [SWAP]     &#9492;&#9472;sda6     2G root  disk  brw-rw----
sr0                                      sr0     1024M root  cdrom brw-rw----

```

I don't to go off-topic, but is mkusb (which I figured out how to install) exclusive to Ubuntu or can it be used in other distros or another unix-like OS? it's just that I used Ubuntu for years and have never heard of this software.

---

### Post by sudodus on 2015-12-11
I'm sorry, but your Kingston pendrive is not seen as a mass storage device. It means that mkusb and several other tools cannot see it and cannot repair it.

- Have you tried in all USB ports of the computer and have you tried in another computer?

- Have you tried the tools suggested by mastablasta in post #6?

If still no success, I'm afraid that the pendrive is damaged beyond repair.

-o-

mkusb is rather new. The very first and simple command line version was published in April 2012.

[Howto make USB boot drives](http://ubuntuforums.org/showthread.php?t=1958073)

It is still not accepted as part of the official repositories, but available via the PPA.

The PPA is exclusive for Ubuntu, but if you get it from [from_phillw.net](https://help.ubuntu.com/community/mkusb/gui#from_phillw.net), you can use it in several other linux distros. It is only a shell-script using some standard built-in programs, and therefore portable between different distros and versions. There is one exception - the method to make *persistent* live drives is only working with Ubuntu and Ubuntu based re-spins.

---

### Post by Sephilin on 2016-01-02
> **sudodus said:**
> I'm sorry, but your Kingston pendrive is not seen as a mass storage device. It means that mkusb and several other tools cannot see it and cannot repair it.

- Have you tried in all USB ports of the computer and have you tried in another computer?

- Have you tried the tools suggested by mastablasta in post #6?

If still no success, I'm afraid that the pendrive is damaged beyond repair.

-o-

mkusb is rather new. The very first and simple command line version was published in April 2012.

[Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")

It is still not accepted as part of the official repositories, but available via the PPA.

The PPA is exclusive for Ubuntu, but if you get it from [from_phillw.net]("https://help.ubuntu.com/community/mkusb/gui#from_phillw.net"), you can use it in several other linux distros. It is only a shell-script using some standard built-in programs, and therefore portable between different distros and versions. There is one exception - the method to make *persistent* live drives is only working with Ubuntu and Ubuntu based re-spins.

Thanks for the link and it's funny how the Datatraveler works well on  Windows 7, but not on Ubuntu atm. Maybe I should try another external hard  drive.

---

