---
title: "Built-in SD Card Slot"
date: 2006-09-29
forum: Hardware &amp; Laptops
---

### Post by bollocks00 on 2006-09-29
I have an IBM Thinkpad Z60t with a built in SD card slot in the front.  Anyone know how I can get this setup and running in linux?

---

### Post by lukew on 2006-09-29
Hi Bollocks,

My 7 in 1 card reader works out of the box. Have you tried? Do you get an error message? What does dmesg | tail state? You might have to mount it manually.

Luke

---

### Post by bollocks00 on 2006-09-29
It doesn't work right now, or at least it doesn't do anything when I put a card in the slot.  dmesg | tail gives:

```

[17179607.512000] NET: Registered protocol family 31
[17179607.512000] Bluetooth: HCI device and connection manager initialized
[17179607.512000] Bluetooth: HCI socket layer initialized
[17179607.564000] Bluetooth: L2CAP ver 2.8
[17179607.564000] Bluetooth: L2CAP socket layer initialized
[17179607.616000] Bluetooth: RFCOMM socket layer initialized
[17179607.616000] Bluetooth: RFCOMM TTY layer initialized
[17179607.616000] Bluetooth: RFCOMM ver 1.7
[17179617.080000] ath0: no IPv6 routers present
[17179622.368000] eth0: no IPv6 routers present

```

How do I go about mounting it manually?

---

### Post by /carlito on 2006-09-30
You should really post the output of lspci so we know what hardware we are talking about.

---

### Post by gigiya on 2006-09-30
I also have problems with my card reader.  I have an Inspiron E1705 and here is my lspci:

> 0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7145
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)0000:0c:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)


I'd appreciate help as well.

---

### Post by /carlito on 2006-09-30
> **gigiya said:**
> I also have problems with my card reader.  I have an Inspiron E1705 and here is my lspci:



I'd appreciate help as well.

The ricoh SD card slots are supported by the 2.6.17 and newer kernels, you should upgrade your kernel version or patch your current kernel!

---

### Post by gigiya on 2006-09-30
I just installed Ubuntu three days ago, and I have since updated the kernel.

---

### Post by bollocks00 on 2006-09-30
Here is my lspci code:
```

lenny@IBM:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
0000:13:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:14:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
0000:14:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
0000:14:00.2 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)

```

---

### Post by /carlito on 2006-10-01
> **bollocks00 said:**
> Here is my lspci code:
```

lenny@IBM:~$ lspci
0000:14:00.2 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)

```


You guys should go to [www.kernel.org](www.kernel.org) and download a 2.6.17 kernel. Unpack your kernel in /usr/src and compile it!

Alternatively you could also updgrade to Edgy. this has a 2.6.17 kernel in its repository's. To do so you should edit /etc/apt/sources.list and change all instances of dapper to edgy. Save the file and run 

```


#sudo apt-get update 
#sudo apt-get upgrade
#sudo apt-get install linux-image-2.6.17-10-generic
```

Good luck!

---

### Post by isTHEr3mOr3 on 2006-10-01
Same problem here:


0000:00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
0000:00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller ( rev 21)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EH CI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridg e (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller ( rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH 4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Rad eon 9600 M10]
0000:02:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:02:04.1 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:02:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Ho st Controller
0000:02:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated Flash Media Controller
0000:02:05.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (re v 02)
0000:02:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)

Any ideas?

---

### Post by /carlito on 2006-10-01
> **isTHEr3mOr3 said:**
> Same problem here:
0000:02:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated Flash Media Controller
 (rev 05)

Any ideas?

You seem to have a Texas Instruments controller. I'm not sure of this, but my guess is that your controller is supported by the 2.6.15 kernel. Could you post the output of "dmesg |tail" after you've plugged in a card?

---

### Post by bollocks00 on 2006-10-02
Updating to Edgy Eft solved the problem.
Thanks!

---

### Post by gigiya on 2006-10-03
> **/carlito said:**
> You guys should go to [www.kernel.org](www.kernel.org) and download a 2.6.17 kernel. Unpack your kernel in /usr/src and compile it!

Alternatively you could also updgrade to Edgy. this has a 2.6.17 kernel in its repository's. To do so you should edit /etc/apt/sources.list and change all instances of dapper to edgy. Save the file and run 

```


#sudo apt-get update 
#sudo apt-get upgrade
#sudo apt-get install linux-image-2.6.17-10-generic
```

Good luck!

I did that and seemed to have seriously screwed up my installation.  When I rebooted after upgrading to Edgy, I just get a brown background with a cursor after logging in normally from the login screen.  I can't boot into failsafe GNOME because it says it can't find the gnome installation.  I boot into the failsafe terminal and can run programs from there (I'm posting from the laptop now.)  In the 2.6.17 kernel my internet doesn't work, but it still works when booting with the 2.6.15-686 kernel.  I have no idea what to do.

---

### Post by bollocks00 on 2006-10-03
Try it again with 'sudo apt-get dist-upgrade' instead of 'sudo apt-get upgrade'

---

### Post by granziliao on 2006-10-04
If your laptop using TI's SD card reader, you don't need upgrade to edgy neither need to upgrade you system kernel just type:

sudo setpci -s 06.2 4c=0x12
In your case, you may use
sudo setpci -s 06.2 4c=0x21

My Laptop is Toshiba Satellite M100 
(PSMA0T-04J01Y) with TI XX12 SD card reader.
Hope this can do some tiny help.

---

### Post by granziliao on 2006-10-04
Sorry, your case should be 
setpci -s 04.3 4c=0x21

---

### Post by granziliao on 2006-10-04
Screenshot:

---

### Post by isTHEr3mOr3 on 2006-10-04
Here's my dmesg |tail
[18379775.936000] SCSI device sda: 241856 2048-byte hdwr sectors (495 MB)
[18379775.936000] sda: Write Protect is off
[18379775.936000] sda: Mode Sense: 38 00 00 00
[18379775.936000] sda: assuming drive cache: write through
[18379775.936000]  sda: sda1
[18379775.936000] sd 5:0:0:0: Attached scsi removable disk sda
[18379775.936000] sd 5:0:0:0: Attached scsi generic sg0 type 0
[18379775.936000] usb-storage: device scan complete
[18379777.476000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[18379996.852000] usb 4-1: USB disconnect, address 10

Didn't make any difference if the card was placed or not. 

Kernel version: 2.6.15-27-386. I think I will try Edgy as well later.

---

### Post by Pointwood on 2006-10-18
I got an IBM Thinkpad Z61T running Kubuntu dapper and my internal card reader doesn't work either :(

lspci output:

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
0000:00:1f.2 0106: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=AHCI (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752M Gigabit Ethernet PCI Express (rev 02)
0000:03:00.0 Network controller: Intel Corporation: Unknown device 4227 (rev 02)
0000:15:00.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:15:00.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:15:00.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:15:00.3 0805: Texas Instruments: Unknown device 803c

dmesg | tail output after adding a card:

[17265135.292000]  4:0:0:0: rejecting I/O to dead device
[17265135.292000] FAT: Directory bread(block 517) failed
[17265135.292000]  4:0:0:0: rejecting I/O to dead device
[17265135.292000] FAT: Directory bread(block 518) failed
[17265135.504000]  4:0:0:0: rejecting I/O to dead device

dmesg | grep hd:

[17264800.008000] SCSI device sdb: 3970049 512-byte hdwr sectors (2033 MB)
[17264800.012000] SCSI device sdb: 3970049 512-byte hdwr sectors (2033 MB)

Maybe it's not worth the trouble before Edgy Eft is released though. It might just be supported there :)

---

### Post by deuce868 on 2006-10-27
Any ideas as to the state of the TI devices? I had thought the new kernel in edgy would support things. I have a HP dv5000t

> $ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d8 (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:06.0 CardBus bridge: Texas Instruments Unknown device 8039
08:06.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
08:06.2 Mass storage controller: Texas Instruments Unknown device 803b
08:06.3 Class 0805: Texas Instruments Unknown device 803c
08:08.0 Ethernet controller: Intel Corporation Intel(R) PRO/100 VE Network Connection (rev 01)


dmesg output:
> 
[17182171.900000] tifm_7xx1: demand removing card from socket 1
[17182175.972000] tifm_7xx1: sd card detected in socket 1


It seems to see the card getting pulled/entered

Any help is appreciated.

---

### Post by jamincollins on 2006-10-30
> **deuce868 said:**
> 
It seems to see the card getting pulled/entered

Any help is appreciated.

I'm seeing the same thing after upgrading to Edgy.  The card reader worked fine under Dapper.  However, under Edgy all I'm getting is the insert and removed messages in dmesg:

> [17185332.512000] tifm_7xx1: sd card detected in socket 3
[17185935.844000] tifm_7xx1: demand removing card from socket 3
[17185939.584000] tifm_7xx1: sd card detected in socket 3

---

### Post by barnogg on 2006-10-30
Hi,

I have exactly the same problem with my Toshiba P100

besides the sound, this is the only thing taht doesnt work.

..alex..

---

### Post by jamincollins on 2006-10-30
Looks like one of the necessary modules isn't being loaded automatically anymore.  I found a working solution at the following post:

[http://ubuntuforums.org/showpost.php?p=1651079&postcount=3](http://ubuntuforums.org/showpost.php?p=1651079&postcount=3)

After running:
  > sudo modprobe tifm_sd

The card is working again.

I'm rather disappointed in the quality of the Dapper to Edgy upgrade so far.  It's not nearly has smooth as I've come to expect from Debian and Debian derivatives.

---

### Post by deuce868 on 2006-10-30
Thanks, that is getting me a bit closer but now I get this dmesg output:

> [17197122.200000] tifm_7xx1: sd card detected in socket 1
[17197122.876000] mmcblk1: unable to set block size to 1024: 4
[17197122.876000] mmcblk: probe of mmc1:b368 failed with error -22


Any ideas?

---

### Post by eightballrj on 2006-10-31
^^^ Same here. My output is the same as the last poster's. Bump for some card reader gurus, haha.

Thanks for any help you can give guys!!

Richard

---

### Post by sportman1280 on 2006-10-31
Dell E1705 laptop, like the other guys.  Edgy is installed.  Card Reader is NOT working :(.  I tried manually loading the modules given, no change.

---

### Post by mcglnx on 2006-11-04
Dell 6400 : Same issue guys!

---

### Post by magic_doc on 2006-11-04
The same here on my Asus Z9100:

```
lspci|grep Ricoh
01:05.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:05.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:05.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
```

This is the SD-Cardreader-Chip built in and seems to be connected to the pcmcia-bus: inserting a sd-card dmesg|tail outputs:

```
[17191978.228000] pccard: PCMCIA card inserted into slot 0
[17191978.228000] pcmcia: registering new device pcmcia0.0

```

modprobe sdhci leads to this:

```
[17191950.724000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[17191950.724000] sdhci: Copyright(c) Pierre Ossman

```

and that´s it!
I also tried to add into /etc/pcmcia/config the following lines:

```
card "Ricoh Bay1Controller"
  version "RICOH", "Bay1Controller"
  bind "ide_cs".

```

which was suggested in some other forum- no effect.

cardctl info says:

```
PRODID_1="RICOH"
PRODID_2="Bay1Controller"
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=254
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

```

I´m running out of ideas, any help would be greatly appreciated!

---

### Post by bengtfalke on 2006-11-06
I have the same problem with the SD card reader. I have a Sony Vaio tx 1 or something and this is the result:

falke@sony:~$ dmesg | tail
[17179617.436000] lo: Disabled Privacy Extensions
[17179617.436000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179617.436000] IPv6 over IPv4 tunneling driver
[17179618.104000] Bluetooth: L2CAP ver 2.8
[17179618.104000] Bluetooth: L2CAP socket layer initialized
[17179618.212000] Bluetooth: RFCOMM socket layer initialized
[17179618.212000] Bluetooth: RFCOMM TTY layer initialized
[17179618.212000] Bluetooth: RFCOMM ver 1.7
[17179622.124000] ipw2200: Firmware error detected.  Restarting.
[17179628.376000] eth1: no IPv6 routers present

I need some hints... I am on the Gartner conference and need to empty my camera card... ;O)

---

### Post by bengtfalke on 2006-11-06
Some more details:
falke@sony:~$ lspci
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
06:05.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:05.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:05.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:08.0 Ethernet controller: Intel Corporation 82562EM/EX/GX - PRO/100 VM (LOM) Ethernet Controller Mobile (rev 03)
06:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
falke@sony:~$ 

regards from Cannes

---

### Post by larsemil on 2006-11-06
i have a hp nc 6000 and this is my only problem right now. 

lspci showns:
```
02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller

```

but this is strange though i have only a sdcardreader. nothing else fits.. 

when putting a card into it dmesg does not change at all.

anyone have any knowledge about this?

---

### Post by rrwo on 2006-11-06
I have a ThinkPad Z60m with a built-in card reader that I cannot get working on Edgy (it never worked in Dapper either).

I've noticed that
```
modprobe mmc_block
```
gives an error: mmc_block is missing.

Could that be the problem?

---

### Post by galileon on 2007-03-09
> **larsemil said:**
> i have a hp nc 6000 and this is my only problem right now. 

lspci showns:
```
02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller

```

but this is strange though i have only a sdcardreader. nothing else fits.. 

when putting a card into it dmesg does not change at all.

anyone have any knowledge about this?

same here, got a TC1100,with a Texas Instrument  PCI1620 PC Card reader, no effects whatsoever on dmesg or system logs when a card is inserted or removed.

---

### Post by Whoopie on 2007-03-09
Hi,

for all users with a Ricoh Bay1Controller card reader, please have a look at [http://www.sf.net/projects/sdricohcs](http://www.sf.net/projects/sdricohcs)

> 
"sdricoh_cs is a Linux driver for Ricoh Bay1Controller Secure Digital and MMC Card Readers that can be found in some notebooks like the Samsung P35."


Best regards,
Whoopie

---

### Post by treesurf on 2007-03-10
I got my TI card reader working by following some of the instructions in the following thread.  I believe there have been a link in there somewhere to a page that had instructions for getting the Ricoh card readers to work as well.

[http://www.ubuntuforums.org/showthread.php?t=315497](http://www.ubuntuforums.org/showthread.php?t=315497)

---

### Post by tyinfitz on 2007-03-22
Firstly i'm a noob, had ubuntu less than a week, but consider myself PC savvy.

I got my inbuilt Ricoh SD card reader in my ASUS M5N laptop working dong the following:

Downloading the file at [http://http://sourceforge.net/projects/sdricohcs]("http://http://sourceforge.net/projects/sdricohcs")

Extracting the files to a temp directory

then in a terminal window...

changing to that directory

running 'make' as advised by the readme.txt file,

then running 'sudo make install' the readme just said to run 'make install' but i've now worked out that sudo means superuser-do and allows the appropriate drivers to be installed and then the reader worked fine after a reboot. My reading has led me to believe that i should unmount the SD card before ejecting as not doing this can cause problems.

I hope this helps, it's what i would've liked to find.

Regards,
tyinfitz.

---

### Post by vkkim on 2007-03-22
Built-in SD card reader in ThinkPad X60s:

lspci:
```
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 09)
15:00.2 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
```

dmesg|tail after card insert:
```
[17212498.372000] mmcblk0: error 2 transferring data
[17212498.372000] end_request: I/O error, dev mmcblk0, sector 0
[17212498.376000] mmcblk0: error 2 transferring data
[17212498.376000] end_request: I/O error, dev mmcblk0, sector 0
```

Help!

---

### Post by jjalocha on 2007-03-30
I have the same problem here under Xubuntu Edgy with the following hardware ([Dell Latitude 131L]("http://www.ubuntuforums.org/showthread.php?t=367898") notebook):

```

$ lspci
> ...
> 08:01.0 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
> 08:01.1 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)

```

After plugging a memory card:

```

$ dmesg
> ...
> [17190107.232000] mmcblk0: mmc0:e624 SD01G 992000KiB 
> [17190107.232000]  mmcblk0: p1

```

```

$ mount
> /dev/sda2 on / type ext3 (rw,errors=remount-ro)
> proc on /proc type proc (rw,noexec,nosuid,nodev)
> /sys on /sys type sysfs (rw,noexec,nosuid,nodev)
> varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
> varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
> procbususb on /proc/bus/usb type usbfs (rw)
> udev on /dev type tmpfs (rw,mode=0755)
> devshm on /dev/shm type tmpfs (rw)
> devpts on /dev/pts type devpts (rw,gid=5,mode=620)
> lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
> /dev/sda4 on /home type ext3 (rw)

```

Note, that my hard drive is device [FONT="Fixedsys"]sda[/FONT].

[FONT="Fixedsys"]modprobe mmc_block[/FONT] gives the same error as above.

I didn't try [http://www.sf.net/projects/sdricohcs](http://www.sf.net/projects/sdricohcs), since this experimental driver is being developed for another device (R5C593 or R5C552, not sure).

---

### Post by jjalocha on 2007-03-31
OK, I got my R5C822 reader working with help of [this link]("http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working"). The 'tifm_sd' module must be loaded into the kernel, adding the following line to the end of the [FONT="Fixedsys"]/etc/modules[/FONT] file:

```

tifm_sd

```

Now I can mount the inserted card manually with:

```

$ sudo mkdir /media/mmc
$ sudo mount /dev/mmcblk0p1 /media/mmc

```

and uninstall it with:

```

$ sudo umount /media/mmc

```

Does anybody know how to configure the system for automatic mounting/unmounting of the card? (I'm using Xubuntu.) According to the link, automount should work already.

[2007-04-05 Edit: Add missing 'mkdir' and 'umount' commands.]

---

### Post by jjalocha on 2007-04-03
It seems not to be a configuration problem, as I had supposed. This issue is reported as [Xfce Bug 2652]("http://bugzilla.xfce.org/show_bug.cgi?id=2652"), and has been solved in later versions. I just hope it's included in Feisty.

---

### Post by silverglade00 on 2007-04-05
> **jjalocha said:**
> OK, I got my R5C822 reader working with help of [this link]("http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working"). The 'tifm_sd' module must be loaded into the kernel, adding the following line to the end of the [FONT="Fixedsys"]/etc/modules[/FONT] file:

```

tifm_sd

```

Now I can mount the inserted card manually with:

```

$ sudo mount /dev/mmcblk0p1 /media/mmc

```

and uninstall it with:

```

 /media/mmc

```

Does anybody know how to configure the system for automatic mounting/unmounting of the card? (I'm using Xubuntu.) According to the link, automount should work already.


```
lspci | grep Ricoh
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

I can confirm this working under Feisty Beta AMD64 on an HP dv2225nr laptop with the above Ricoh reader. The only thing I had to change from your instructions is to manually create the folder /media/mmc as root. I also need to know how to automate the mounting if anyone knows. I can do it manually with no problems however.

---

### Post by jjalocha on 2007-04-05
silverglade00, you are right, you must create /media/mmc (or whatsoever) with sudo first.

It is not clear to me, if you are running Xubuntu or Ubuntu. In case of Ubuntu, it should be mounted automatically. Xfce is broken in that respect, and you have to mount it manually. (See [Xfce Bug 2652]("http://bugzilla.xfce.org/show_bug.cgi?id=2652").)

---

### Post by silverglade00 on 2007-04-09
I am running Ubuntu. I have it working great now thanks to this thread. I added the Disk Mounter applet to my Panel and now I can play with my SD cards at will. All is good in the land of Linux.

---

