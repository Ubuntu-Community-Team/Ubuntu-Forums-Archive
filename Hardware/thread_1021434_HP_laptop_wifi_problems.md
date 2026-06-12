---
title: "HP laptop wifi problems"
date: 2008-12-25
forum: Hardware
---

### Post by Mr_Samsa on 2008-12-25
Hello.

Today I received a HP G50-109NR. It has an AR242x 802.11abg wireless card. 

Anyway, I installed Ubuntu 8.10 through wubi on a copy of Vista Premium. In Vista the wireless card seems to work, but I can't seem to get it to work in Ubuntu. One peculiar thing I've noticed is that the button which is used to turn the wifi on does not seem to be responding. In Vista, when the wifi is on the button shines blue, this does not happen while I am using Ubuntu. 


Does anyone know of a way in which I could force my wireless card on? 

Thanks in advance.

Happy Holidays!

---

### Post by pytheas22 on 2008-12-25
With some cards--and if I recall correctly with the AR242x cards in particular--the LED light doesn't function properly, although the wireless itself should work.  There's a solution somewhere for the LED that I can find once we solve the larger problem.

AR242x should work (with the exception of the LED) out-of-the-box on Ubuntu 8.10, however.  Please post the output of these commands so that we can figure out why it's not working for you:
```

sudo iwlist scan
dmesg | tail -50
dmesg | grep -e wlan -e ath -e adio
lshw -C Network
uname -m
```

---

### Post by Mr_Samsa on 2008-12-25
Okay, these were my results:

```
auxillaryhammer@ubuntu:~$ sudo iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

pan0      Interface doesn't support scanning. 

auxillaryhammer@ubuntu:~$ dmesg | tail -50 
[   39.243374] Bluetooth: RFCOMM ver 1.10 
[   39.245245] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[   39.245253] Bluetooth: BNEP filters: protocol multicast 
[   39.292074] Bridge firewalling registered 
[   39.292356] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature. 
[   39.313193] Bluetooth: SCO (Voice Link) ver 0.6 
[   39.313207] Bluetooth: SCO socket layer initialized 
[   42.041293] mtrr: base(0xc5000000) is not aligned on a size(0xe00000) boundary 
[   43.654124] NET: Registered protocol family 17 
[   65.531743] CPU0 attaching NULL sched-domain. 
[   65.531765] CPU1 attaching NULL sched-domain. 
[   65.541100] CPU0 attaching sched-domain: 
[   65.541112]  domain 0: span 0-1 level CPU 
[   65.541119]   groups: 0 1 
[   65.541131] CPU1 attaching sched-domain: 
[   65.541136]  domain 0: span 0-1 level CPU 
[   65.541141]   groups: 1 0 
[  130.037526] type=1503 audit(1230252096.296:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5894/net/" pid=5894 profile="/usr/sbin/cupsd" 
[  130.128460] NET: Registered protocol family 10 
[  130.129911] lo: Disabled Privacy Extensions 
[  130.158116] type=1503 audit(1230252096.416:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5894 profile="/usr/sbin/cupsd" 
[  130.158149] type=1503 audit(1230252096.416:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5894 profile="/usr/sbin/cupsd" 
[  130.158169] type=1503 audit(1230252096.416:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5894 profile="/usr/sbin/cupsd" 
[  130.158184] type=1503 audit(1230252096.416:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5894 profile="/usr/sbin/cupsd" 
[  130.158198] type=1503 audit(1230252096.416:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5894 profile="/usr/sbin/cupsd" 
[  130.158214] type=1503 audit(1230252096.416:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5894 profile="/usr/sbin/cupsd" 
[  130.158228] type=1503 audit(1230252096.416:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5894 profile="/usr/sbin/cupsd" 
[  130.158248] type=1503 audit(1230252096.416:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5894 profile="/usr/sbin/cupsd" 
[  130.158385] type=1503 audit(1230252096.416:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5894/net/dev" pid=5894 profile="/usr/sbin/cupsd" 
[  140.416033] eth0: no IPv6 routers present 
[  474.955780] usb 2-4: USB disconnect, address 2 
[  483.577897] usb 4-3: USB disconnect, address 2 
[  627.708039] usb 4-4: new high speed USB device using ehci_hcd and address 4 
[  627.846787] usb 4-4: configuration #1 chosen from 1 choice 
[  627.849385] scsi6 : SCSI emulation for USB Mass Storage devices 
[  627.851453] usb-storage: device found at 4 
[  627.851466] usb-storage: waiting for device to settle before scanning 
[  632.848519] usb-storage: device scan complete 
[  632.850159] scsi 6:0:0:0: Direct-Access     Corsair  Flash Voyager    1100 PQ: 0 ANSI: 0 CCS 
[  632.857711] sd 6:0:0:0: [sdb] 7864320 512-byte hardware sectors (4027 MB) 
[  632.859838] sd 6:0:0:0: [sdb] Write Protect is off 
[  632.859853] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00 
[  632.859859] sd 6:0:0:0: [sdb] Assuming drive cache: write through 
[  632.863327] sd 6:0:0:0: [sdb] 7864320 512-byte hardware sectors (4027 MB) 
[  632.864824] sd 6:0:0:0: [sdb] Write Protect is off 
[  632.864840] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00 
[  632.864845] sd 6:0:0:0: [sdb] Assuming drive cache: write through 
[  632.864858]  sdb: sdb1 
[  632.901869] sd 6:0:0:0: [sdb] Attached SCSI removable disk 
[  632.902079] sd 6:0:0:0: Attached scsi generic sg2 type 0 
auxillaryhammer@ubuntu:~$ dmesg | grep -e wlan -e ath -e adio 
[   14.882496] ath_hal: module license 'Proprietary' taints kernel. 
[   14.962656] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413) 
[   14.996115] wlan: 0.9.4 
[   15.017864] ath_pci: 0.9.4 
[   15.025911] ath_pci 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23 
[   15.025928] ath_pci 0000:07:00.0: setting latency timer to 64 
[   20.200317] ath_pci 0000:07:00.0: PCI INT A disabled 
auxillaryhammer@ubuntu:~$ lshw -C Network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: MCP78S [GeForce 8200] Ethernet 
       vendor: nVidia Corporation 
       physical id: a 
       bus info: pci@0000:00:0a.0 
       logical name: eth0 
       version: a2 
       serial: 00:1d:72:7d:e3:20 
       width: 32 bits 
       clock: 66MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: AR242x 802.11abg Wireless PCI Express Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:07:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: cap_list 
       configuration: latency=0 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 3 
       logical name: pan0 
       serial: 26:62:59:6a:e2:c9 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 
auxillaryhammer@ubuntu:~$ uname -m 
i686 
```

---

### Post by pytheas22 on 2008-12-25
Please try running these commands:

```
sudo apt-get update
sudo apt-get install linux-backports-modules-intrepid
```

Then reboot.  Does this fix the problem?  According to this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/289912"), it should.  But if it doesn't, we can try other things.

---

### Post by Mr_Samsa on 2008-12-25
Thanks for the advice. Unfortunately, I am not able to connect this computer to the Internet (Do to circumstances of my location in the middle of nowhere, I am unable to connect this laptop via ethernet.) In order to download anything for this laptop, I must first download it on a separate computer.

Is there any way I could download these files and then put them on a flash drive and carry them over to my laptop?

---

### Post by pytheas22 on 2008-12-25
Installing that package without an Internet connection would be quite a hassle, so before I make you do that, please try this other possible solution instead:

In [this thread]("http://ubuntuforums.org/showthread.php?t=798485"), there's a script for installing the madwifi (Atheros) drivers from source, which is likely to solve your problem.  If you scroll down on that page, you'll find instructions for running the script without any Internet connection available.  The instructions may be a little convoluted, so if you don't understand all of them, let me know.  Otherwise, please try following them so that you get a newer version of madwifi installed, then reboot Ubuntu.  Does this resolve your problem?

If not, or if you don't want to try that script, I can give you directions for installing linux-backports-modules-intrepid by hand, but it will involve a lot of tedious downloading of individual packages from [http://packages.ubuntu.com](http://packages.ubuntu.com).

---

### Post by itkeepsrepeating on 2009-02-03
pytheas22, I have the same laptop mentioned by OP, and gave up on it a few weeks after purchasing [black friday]. If you're still available to assist, I'll give it another shot this week sometime. In the meantime, I've given *gasp* Win7 beta a run. In any case, I want to use the 64-bit version of intrepid in order to utilize the full 4 GB of RAM I've installed [upgraded]. 

I can plug this laptop into my router to get internet until I [read: you with my fingers] can fix the wireless, but is the backports solution suitable for 64-bit?

In the event it can help others with this laptop or the people helping the other owners, here is an excerpt of the Belarc page [from within Vista] from this machine:
```
Operating System 	  	System Model
Windows Vista Home Premium Service Pack 1 (build 6001) 	  	Hewlett-Packard HP G50 Notebook PC F.24
System Serial Number: 2CE838CJY4
Enclosure Type: Notebook
Processor a 	  	Main Circuit Board b
1.90 gigahertz AMD Athlon Dual-Core QL-60
64 kilobyte primary memory cache
1024 kilobyte secondary memory cache 	  	Board: Wistron 360A 08.40
Bus Clock: 133 megahertz
BIOS: Hewlett-Packard F.24 09/03/2008
Drives 	  	Memory Modules c,d
120.03 Gigabytes Usable Hard Drive Capacity
40.06 Gigabytes Hard Drive Free Space

NF0005F UVY205G SCSI CdRom Device [CD-ROM drive]
NF0005F UVY205G SCSI CdRom Device [CD-ROM drive]
Slimtype DVD A DS8A2S-A ATA Device [CD-ROM drive]

Generic- Multi-Card USB Device [Hard drive] (3.96 GB) -- drive 1
WDC WD1200BEVS-60UST0 ATA Device [Hard drive] (120.03 GB) -- drive 0 	  	2814 Megabytes Installed Memory

Slot 'S1' has 2048 MB
Slot 'S2' has 2048 MB
  	Local Drive Volumes
  	
		
c: (NTFS on drive 0) 	68.08 GB 	13.27 GB free
d: (NTFS on drive 0) 	10.58 GB 	1.86 GB free
i: (NTFS on drive 0) 	41.37 GB 	24.93 GB free
  	Network Drives
  	None detected
Users (mouse over user name for details) 	  	Printers
local user accounts	last logon
 tatertom 	2/3/2009 1:45:05 AM 	(admin)
local system accounts
 Administrator 	10/8/2008 9:13:56 PM 	(admin)
 Guest 	1/17/2009 10:18:35 AM 	

DISABLED Marks a disabled account;   LOCKED OUT Marks a locked account
	  	
Adobe PDF Converter 	on Documents\*.pdf
Microsoft XPS Document Writer 	on XPSPort:
Controllers 	  	Display
ATA Channel 0 [Controller] (2x)
ATA Channel 1 [Controller] (2x)
Standard Dual Channel PCI IDE Controller (2x) 	  	NVIDIA GeForce 8200M G [Display adapter]
Generic PnP Monitor (15.4"vis)
Bus Adapters 	  	Multimedia
Microsoft iSCSI Initiator
SCSI/RAID Host Controller
Standard Enhanced PCI to USB Host Controller (2x)
Standard OpenHCD USB Host Controller (2x) 	  	Conexant High Definition SmartAudio 221
NVIDIA HDMI Audio
Communications 	  	Other Devices
HDAUDIO Soft Data Fax Modem with SmartCP

		
6TO4 Adapter
Atheros AR5007 802.11b/g WiFi Adapter
	Auto IP Address: 	192.168.3.149 / 24
	Gateway: 	192.168.3.1
	Dhcp Server: 	192.168.3.1
	Physical Address: 	00:23:4D:2E:65:54
isatap.{355556DE-1F29-4CC3-AD9E-B4510E5FC3A3}
isatap.{EC637A8B-56AF-4C9B-95B1-5C38DC0DB8B9}
NVIDIA nForce 10/100/1000 Mbps Networking Controller
	Dhcp Server: 	none responded
	Physical Address: 	00:1D:72:7D:1E:48
Teredo Tunneling Pseudo-Interface
 
Networking Dns Server: 	192.168.3.1
	  	Microsoft AC Adapter
Microsoft ACPI-Compliant Control Method Battery
HID-compliant consumer control device
HID-compliant device (2x)
USB Human Interface Device (2x)
HID Keyboard Device
Standard PS/2 Keyboard
HID-compliant mouse
Synaptics PS/2 Port TouchPad [Mouse]
Realtek USB 2.0 Card Reader
USB Composite Device
USB Root Hub (4x)
Generic volume shadow copy
Multi-Card

```
It may also be relevant to know I use a usb wireless mouse/keyboard, and the extra partition is Windows 7, and will be replaced by Ubuntu for this application.

---

### Post by pytheas22 on 2009-02-03
itkeepsrepeating: yes, in principle, installing the backports package should solve the problem, so hook Ubuntu up to the Internet and type:
```

sudo apt-get update
sudo apt-get install linux-backports-modules-intrepid
```

Then reboot.  Is the problem solved?  If not, please post the output of these commands, in this order, and we'll try some other solutions:

```
lsmod | grep ath
sudo rmmod ath_pci
sudo rmmod ath9k
sudo rmmod ath5k
sudo modprobe ath5k
dmesg | tail -50
sudo iwlist scan
dmesg | grep -e ath -e wlan
lspci -nn | grep -i atheros
```

---

### Post by sdegrace on 2009-03-01
Pytheas22, I want to say thank you. I spent many fruitless hours on madwifi-project.org (and many hours before than until I figured out where madwifi.org went - they moved without leaving a forwarding address!!) building different versions of ath_pci, and it turned out with by HP G50 laptop in Intrepid, it almost worked out of the box and only needed the linux-backports-modules-intrepid! Now the wireless is perfect except for the LED light, which would be nice if it worked but I can live without. I had to hunt a long time before I found your good advice!

---

### Post by pytheas22 on 2009-03-01
sdegrace: I'm glad it worked :)

As for the madwifi site, unfortunately some fascist basically hijacked their domain a few months ago and replaced the real website with something that looks like it was made by someone just learning html, and which is filled with extremely erroneous and outdated information.  The real madwifi project now has [http://madwifi-project.org/](http://madwifi-project.org/).  Just thought I'd point this out in case it helps anyone else.

---

### Post by solidsnakedoc on 2009-03-01
will these commands work with all wifi cards

sudo apt-get update
sudo apt-get install linux-backports-modules-intrepid

---

### Post by sdegrace on 2009-03-02
I think that maybe the particular fix addresses a problem with support for specific Atheros chipsets in Intrepid... but it doesn't hurt to try.

---

### Post by pytheas22 on 2009-03-02
> 
will these commands work with all wifi cards

sudo apt-get update
sudo apt-get install linux-backports-modules-intrepid

No, this fix only works with cards that are supported by the ath9k module, which includes only newer Atheros-based devices; this also only applies to Ubuntu 8.10, not earlier versions (On the other hand, those commands won't hurt anything, so you can give them a try if you like.  Make sure to reboot your computer for changes to take effect.)

If you need help getting a wireless card to work that's not supported by ath9k, post the output of these commands and I'll provide instructions:
```

lspci -nn
lsusb
lshw -C Network
uname -rm
```

---

### Post by spikenick on 2009-03-03
I know that once upon a time I found a command to turn the LED from amber to blue on HP DV6700. I now use the ath5k driver since I had began testing for 9.04 does anybody know of a way to turn this on, or even better a script someone might have that changes the LED based on link state.

---

### Post by pytheas22 on 2009-03-04
spikenick: [this]("http://knowledge76.com/index.php/Wireless_LED_on_Ubuntu") might work, although I think it probably applies only to Asus laptops--but you might be able to modify the line that reads:
```

WIRELESS_LED=/proc/acpi/asus/wled
```

to point it to the equivalent for HP laptops (i.e., something like /proc/acpi/hp/wled--I'm not sure of the exact path because I don't own an HP laptop, but if you look around /proc, you might find it).

---

### Post by itkeepsrepeating on 2009-04-13
It may be worthy to note:

Jaunty boots to live, installs, and runs great as of sometime last week on the g50-109nr. No fidgeting with the wireless at all. The wifi button-light stays red, but functions to turn the wireless on and off. I am fine with that for my purposes.

The only annoyance I have is the touchpad's on/off button-light changes colors [white-on/red-off] but doesn't function. As a matter of preference, I like to shut it off and use a mouse, in order to keep my palms from tapping it while typing. I'm off to hunt that down now. :-\"

---

