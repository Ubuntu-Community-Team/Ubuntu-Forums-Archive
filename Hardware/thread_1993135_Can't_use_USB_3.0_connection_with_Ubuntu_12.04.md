---
title: "Can't use USB 3.0 connection with Ubuntu 12.04"
date: 2012-06-01
forum: Hardware
---

### Post by rewyllys on 2012-06-01
**Background**
Recently my 1.0TB external hard drive--my backup drive--failed, and I replaced it with a 2.0TB external HD that is USB 3.0-capable.  I use the 2.0TB HD for daily backups by Lucky Backup from my Ubuntu 12.04 system, and also for occasional backups from my rarely used Windows Vista system.  The new external HD is formatted NTFS.

**The Problem**
Though the 2.0TB drive is accessible and usable when plugged into a USB 2.0 port using Ubuntu 12.04, I have so far been unable to see the drive when it is plugged into a USB 3.0 port.  I would like to be able to utilize the higher speed of USB 3.0 when I use the new drive, and will appreciate any and all suggestions of how to do so.

Here is the output I get when I enter “lsusb” at the command line:

```
ron@ron-desktop-linux:~$ sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 005: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 003 Device 002: ID 0d9f:0002 Powercom Co., Ltd Black Knight PRO / WOW Uninterruptible Power Supply (Cypress HID->COM RS232)
Bus 008 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 002 Device 006: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
```

It appears that Ubuntu is recognizing the 3.0 port, i.e., as “Bus 010 Device 001”.  But I'm not sure about this, and I have no idea what to try next.

Thanks in advance for any and all help.

---

### Post by Redblade20XX on 2012-06-01
Just a suggestion can you post the output of ```
lspci
```. Just want to see if Ubuntu recognises the port.

-Red

---

### Post by rewyllys on 2012-06-01
Here is the output from lspci:

```
ron@ron-desktop-linux:~$ sudo lspci
[sudo] password for ron: 
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:05.0 FireWire (IEEE 1394): LSI Corporation FW322/323 (rev 70)
02:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
04:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8500 GT] (rev a1)
ron@ron-desktop-linux:~$ 
```

The next-to-last line of the output appears to show recognition of USB 3.0, if I'm interpreting it correctly.

---

### Post by Cheesemill on 2012-06-01
Can you run
```
sudo dmesg -C
```
then plug in the drive and post the output of
```
dmesg
```

---

### Post by rewyllys on 2012-06-01
> **Cheesemill said:**
> Can you run
```
sudo dmesg -C
```
then plug in the drive and post the output of
```
dmesg
```

Thanks for your suggestions.

I ran "sudo dmesg -C".  There was no visible output.
Next, I ran "sudo dmesg".  No output.
Next, I ran "sudo dmesg -c".  Again, no output.
Next, I ran "sudo dmesg -E".  Still no output.

What else should I try?

---

### Post by Redblade20XX on 2012-06-01
Try this one and post the output with the drive connected to the 3.0 port.
```
usb-devices
```

-Red

---

### Post by rewyllys on 2012-06-03
> **Redblade20XX said:**
> Try this one and post the output with the drive connected to the 3.0 port.
```
usb-devices
```

-Red
Here's the output from issuing "usb-devices":
```
ron@ron-desktop-linux:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.02
S:  Manufacturer=Linux 3.2.0-23-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=10 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 2
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.02
S:  Manufacturer=Linux 3.2.0-23-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:02:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.02
S:  Manufacturer=Linux 3.2.0-23-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1307 ProdID=0165 Rev=01.00
S:  Manufacturer=USB 2.0
S:  Product=USB Flash Drive
S:  SerialNumber=abe63a52ac314a
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=058f ProdID=6362 Rev=01.00
S:  Manufacturer=Generic
S:  Product=Mass Storage Device
S:  SerialNumber=058F312D81B1
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=01 Prnt=01 Port=07 Cnt=03 Dev#=  6 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0409 ProdID=0058 Rev=01.00
S:  Manufacturer=NEC Corporation
S:  Product=USB2.0 Hub Controller
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=06 Port=03 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=058f ProdID=6366 Rev=01.00
S:  Manufacturer=Generic
S:  Product=Mass Storage Device
S:  SerialNumber=058F0O1111B1
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-23-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0d9f ProdID=0002 Rev=00.00
S:  Manufacturer=POWERCOM CO., LTD.
S:  Product=USB to Serial
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=03(HID  ) Sub=00 Prot=00 Driver=(none)

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-23-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-23-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-23-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-23-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=08 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-23-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=08 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=067b ProdID=2303 Rev=03.00
S:  Manufacturer=Prolific Technology Inc.
S:  Product=USB-Serial Controller
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=00 Driver=pl2303

T:  Bus=09 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.02
S:  Manufacturer=Linux 3.2.0-23-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:02:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

```

(Sorry for my slow response -- had to spend yesterday and most of today on family matters.)

---

### Post by Redblade20XX on 2012-06-03
Can't see nothing yet. One more attempt. Restart the computer without the drive attached. Once the computer finishes booting, go into /var/log and look for a file named kern.log. This file will contain all events that the kernel has seen. Open it in gedit. Plug the drive back in while the file is open in gedit. Gedit should then notify you if there were any changes in the file signifying that it most likely detected the device. If it did detected it, something about a usb should be written in the file. 

-Red

---

### Post by rewyllys on 2012-06-04
Thanks for your continued suggestions.

Here are the pertinent lines from the kern.log file following my plugging the 2.0TB USB cable into the USB 3.0 port:
```
Jun  4 17:20:17 ron-desktop-linux kernel: [  264.272045] hub 8-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Jun  4 17:20:17 ron-desktop-linux kernel: [  264.272051] usb 8-1: USB disconnect, device number 2
Jun  4 17:20:17 ron-desktop-linux kernel: [  264.272211] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
Jun  4 17:20:17 ron-desktop-linux kernel: [  264.272227] pl2303 8-1:1.0: device disconnected
Jun  4 17:20:17 ron-desktop-linux kernel: [  264.512015] usb 8-1: new full-speed USB device number 3 using uhci_hcd
Jun  4 17:20:17 ron-desktop-linux kernel: [  264.673214] pl2303 8-1:1.0: pl2303 converter detected
Jun  4 17:20:17 ron-desktop-linux kernel: [  264.685226] usb 8-1: pl2303 converter now attached to ttyUSB0
```
I guess the system now sees the USB 3.0 port.

---

### Post by Redblade20XX on 2012-06-04
From the looks of it, I think the port maybe damaged. :(
From the first line, the kernel forced activation of the port
which means that it was disabled through hardware.
But as one last attempt, look into you BIOs to see if maybe the
port is disabled.

-Red

---

### Post by typhoon_tip on 2012-06-04
We usually all fall in the same problem.

Does your USB cable have dual power supply on the PC side ? If not, get one. I have always the same problem (we are an IT company), and 99% of the time the port is not damaged, just the power suddenly is not enough and need to use a "3 way" cable (or external power into the drive).

To be clear, the cable I am mentioning:
[IMG]http://bixnet.net/images/Cab-USB-YBlack.jpg[/IMG]

Not sure if there are USB 3.0 cables like this, tough. The fact that you changed HD, means the power may not be enough anymore. The fact that it comes on then off, is very likely to be a power issue, pal.

Cheers. ):P

---

### Post by Nattydread69 on 2012-06-13
@typhoon_tip

Hey man you are a lifesaver! I have been scratching my head for a week why ubuntu couldn't see my external hard drive and the answer was that I had to plug in both the wires into my desktop USB ports.
I just thought it was a software bug as it was fine with my laptop with only one port used.
By the way they were USB 2 not 3.

Thanks so much!

---

### Post by typhoon_tip on 2012-06-13
> **Nattydread69 said:**
> @typhoon_tip

Hey man you are a lifesaver! I have been scratching my head for a week why ubuntu couldn't see my external hard drive and the answer was that I had to plug in both the wires into my desktop USB ports.
I just thought it was a software bug as it was fine with my laptop with only one port used.
By the way they were USB 2 not 3.

Thanks so much!

Loll happy to help ! Fell into this c**p more times than I dare to remember, first: no panic. Is very unlikely a USB get damaged.

:guitar:

---

### Post by ewb on 2012-06-14
Did the dual cable also solve the OPs problem?

I have a similar issue, and perhaps a similar machine to the OP:  It is a circa 2008 box with the intel ICH9 chipset, to which I have added a PCIe 1X card with the "NEC" USB 3.0 chip on it.  In fact, I have tried 2 of these now from different mfgrs. Both have a 4-pin molex power connector which I am using (presumably solving the power issue as well as the dual cable?).  I am unable to get a SuperSpeed connection to a Kingston DT Ultimate USB 3.0 flash stick. I always get a "high-speed" connection and the driver is always xhci_hcd: From syslog:

```

Jun 14 14:37:45 kennebec kernel: [  167.568015] usb 9-2: new high-speed USB device number 2 using xhci_hcd

```Running Ubuntu 12.04 amd64, kernel 3.2.0-25-generic.  Mobo is ASUS P5E WS with 2 PCIe 2.0 slots (x16) and 1 x1 slot that *may* only be PCIe 1.1.  I have tried to use both an x16 slot and the x1 slot with the identical outcome.

I have tried the latest 3.4 mainline kernel also (3.4.0-030400-generic_3.4.0-030400.201205210521_amd64) - same result.

I also have a newer laptop that boots Win7 & Ubuntu 12.04 (Toshiba Portege). This has a "built-in" USB 3.0 port and lspci says it also has the NEC controller chip (uPD720200 in lspci -v).   On this machine, under ubuntu I *do* get a SuperSpeed connection (every time). I also apparently get a SuperSpeed connection under Win7 (The only way I know to tell this is a speed test - Seq. Read at 100+ Mbytes/sec).

I am beginning to think that the ICH9 PCI implementation is the culprit and perhaps the NEC chip and the ICH9 don't get along - or perhaps it is this mobo, or (hopefully) it is some subtle issue in the driver?

Any ideas?

---

### Post by Cybertib on 2012-06-16
> **Redblade20XX said:**
> Can't see nothing yet. One more attempt. Restart the computer without the drive attached. Once the computer finishes booting, go into /var/log and look for a file named kern.log. This file will contain all events that the kernel has seen. Open it in gedit. Plug the drive back in while the file is open in gedit. Gedit should then notify you if there were any changes in the file signifying that it most likely detected the device. If it did detected it, something about a usb should be written in the file. 

-Red

Hello from France, 

I have the same problem. However, the /var/log/kernel.log is not modified while pluging my hard drive into the USB 3 port. However, power supply works. 

Cheers, 
Thibault

---

### Post by d.atanasov on 2012-06-16
> **typhoon_tip said:**
> We usually all fall in the same problem.

Does your USB cable have dual power supply on the PC side ? If not, get one. I have always the same problem (we are an IT company), and 99% of the time the port is not damaged, just the power suddenly is not enough and need to use a "3 way" cable (or external power into the drive).
....
Cheers. ):P
Hi [typhoon_tip]("http://ubuntuforums.org/member.php?u=1183490"), 

Do you think this could happen to eSATA external drives too? I have an external drive with USB 2.0 and eSATA ports. When I`m using the eSATA the drive from time to time goes down... Do you think that the power supply is also a good chose to check why this is happens ?  

Thanks in advance. 

cheers

---

### Post by typhoon_tip on 2012-06-16
> **d.atanasov said:**
> Hi [typhoon_tip]("http://ubuntuforums.org/member.php?u=1183490"), 

Do you think this could happen to eSATA external drives too? I have an external drive with USB 2.0 and eSATA ports. When I`m using the eSATA the drive from time to time goes down... Do you think that the power supply is also a good chose to check why this is happens ?  

Thanks in advance. 

cheers

I think it can... Does your eSata box have an external, separate power supply jack that you can plug in ? Or just the data ports ?

---

### Post by d.atanasov on 2012-06-17
Yes, It has external power cable and it cannot be run without it plugged into the net.  This I guess should be enough power. I will try tomorrow to plug the both cables.

---

