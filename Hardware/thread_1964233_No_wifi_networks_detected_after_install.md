---
title: "No wifi networks detected after install"
date: 2012-04-23
forum: Hardware
---

### Post by Johnny Vox on 2012-04-23
Hi all! Forgive me if this has been answered before--I tried googling solutions to this and the only answers I found were confusing at best.

Brand new to Linux. Just got Ubuntu installed (with a bit of trouble) on my old laptop the other day. Windows still works perfectly but Unbuntu doesn't find any wireless networks. It also wouldn't work when I plugged the ethernet cable in directly.

Windows Vista 32 bit, Intel Core Duo t5750 2Ghz, 3 gigs ram. Dell Inspiron 1525.

---

### Post by ahallubuntu on 2012-04-23
You've probably got a "Dell" wireless card in there aka a Broadcom card.  Unfortunately not all wireless cards play well with Ubuntu.  (Blame the wireless card manufacturers for poor support.)

Here's a solution I found here:

[http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/](http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/)


Verify that you really have a bcm4311 wireless card (and not the Intel card) installed according to that page - then solution is to run these steps in a terminal window:

sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo apt-get remove bcmwl-kernel-source
sudo reboot

---

### Post by Johnny Vox on 2012-04-23
> **ahallubuntu said:**
> You've probably got a "Dell" wireless card in there aka a Broadcom card.  Unfortunately not all wireless cards play well with Ubuntu.  (Blame the wireless card manufacturers for poor support.)

Here's a solution I found here:

[http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/](http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/)


Verify that you really have a bcm4311 wireless card (and not the Intel card) installed according to that page - then solution is to run these steps in a terminal window:

sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo apt-get remove bcmwl-kernel-source
sudo reboot

Thanks so much, I'm at work right now but I'll try this when I get home and see if it works!

---

### Post by Johnny Vox on 2012-04-23
> **Johnny Vox said:**
> Thanks so much, I'm at work right now but I'll try this when I get home and see if it works!

So I gave it a shot in the Ubuntu terminal and it asks for my password? Any ideas?

---

### Post by grahammechanical on 2012-04-23
You want us to guess your password?

It is the one you set when you installed Ubuntu. Just type it in. Nothing will appear in the terminal screen - security reasons. Then press enter. If you type it wrong, terminal will tell you.

Regards.

---

### Post by Johnny Vox on 2012-04-23
> **grahammechanical said:**
> You want us to guess your password?

It is the one you set when you installed Ubuntu. Just type it in. Nothing will appear in the terminal screen - security reasons. Then press enter. If you type it wrong, terminal will tell you.

Regards.

Duh, sorry. I must have typed wrong 3 times because I got errors! Haha, it would be pretty entertaining to hear some guesses on what it is though :)

Ok, here was the log after I typed in the command, sorry for the length:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Dell Device 022f
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0a <?>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 022f
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at fea00000 (64-bit, non-prefetchable) [size=1M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at eff8 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 3
	Kernel driver in use: i915
	Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
	Subsystem: Dell Device 022f
	Flags: bus master, fast devsel, latency 0
	Memory at feb00000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Device 022f
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6f20 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Device 022f
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 6f00 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Device 022f
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 022f
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe800000-fe8fffff
	Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Dell Device 022f
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: fe700000-fe7fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000c01fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Dell Device 022f
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fe400000-fe6fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Dell Device 022f
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Device 022f
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6f80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Device 022f
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 6f60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Device 022f
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 6f40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Device 022f
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	Memory behind bridge: fe300000-fe3fffff
	Capabilities: [50] Subsystem: Dell Device 022f

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
	Subsystem: Dell Device 022f
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 022f
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 6fa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Device 022f
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
	I/O ports at 6eb0 [size=8]
	I/O ports at 6eb8 [size=4]
	I/O ports at 6ec0 [size=8]
	I/O ports at 6ec8 [size=4]
	I/O ports at 6ee0 [size=32]
	Memory at fe9fb800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/4 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
	Subsystem: Dell Device 022f
	Flags: medium devsel, IRQ 10
	Memory at fe9fb700 (32-bit, non-prefetchable) [size=256]
	I/O ports at 10c0 [size=32]
	Kernel modules: i2c-i801

02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: Dell Device 022f
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at fe3ff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
	Subsystem: Dell Device 022f
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at fe3ff500 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Dell Device 022f
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at fe3ff600 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
	Subsystem: Dell Device 022f
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at fe3ff700 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: r852
	Kernel modules: r852

09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
	Subsystem: Dell Device 022f
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at de00 [size=256]
	Capabilities: [48] Power Management version 3
	Capabilities: [5c] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [c0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [130] Device Serial Number 88-5a-e2-ff-ff-9b-21-00
	Kernel driver in use: sky2
	Kernel modules: sky2

0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
	Subsystem: Dell Wireless 1395 WLAN Mini-Card
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe7fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information: Len=78 <?>
	Capabilities: [e8] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Virtual Channel
	Capabilities: [160] Device Serial Number 0f-ab-69-ff-ff-32-00-22
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

---

### Post by ahallubuntu on 2012-04-23
So this output confirms you have the BCM4312 card (close enough to the 4311):

> 0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
Subsystem: Dell Wireless 1395 WLAN Mini-Card

So go ahead and type these commands from above:

```
sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo apt-get remove bcmwl-kernel-source
sudo reboot
```

---

### Post by Johnny Vox on 2012-04-23
> **ahallubuntu said:**
> So this output confirms you have the BCM4312 card (close enough to the 4311):



So go ahead and type these commands from above:

```
sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo apt-get remove bcmwl-kernel-source
sudo reboot
```

Sorry, I should have been more thorough--I typed these and it didn't work. Looked like it tried to connect to the internet to get the updates and couldn't.

---

### Post by ahallubuntu on 2012-04-23
Ugh.  Are you sure wired ethernet doesn't work?  Plug your ethernet cable in again.  That Marvell ethernet adapter seems to work out of the box for others on Ubuntu 11.10 .

Look in the upper right corner for a network connection icon if it doesn't automatically connect.  Look for "Auto Eth0" or something like that and try to connect.

Anyway, if you can get a wired connection to the internet, try those commands again.

---

### Post by Johnny Vox on 2012-04-23
> **ahallubuntu said:**
> Ugh.  Are you sure wired ethernet doesn't work?  Plug your ethernet cable in again.  That Marvell ethernet adapter seems to work out of the box for others on Ubuntu 11.10 .

Look in the upper right corner for a network connection icon if it doesn't automatically connect.  Look for "Auto Eth0" or something like that and try to connect.

Anyway, if you can get a wired connection to the internet, try those commands again.

Ok I'll try the wired connection again when I get a chance. Here was the error from those commands FYI. 

Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease](http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ahallubuntu on 2012-04-23
Right - I know it won't work without an internet connection, because it's going to download stuff from the internet to update your wireless driver.

There are ways to make this work without an internet connection, but it's kind of detailed (I googled for it).

Yuck, I hate Broadcom wireless cards!  I've never had to do this with an Intel card - they just work automatically in Linux...

---

### Post by Johnny Vox on 2012-04-23
> **ahallubuntu said:**
> Right - I know it won't work without an internet connection, because it's going to download stuff from the internet to update your wireless driver.

There are ways to make this work without an internet connection, but it's kind of detailed (I googled for it).

Yuck, I hate Broadcom wireless cards!  I've never had to do this with an Intel card - they just work automatically in Linux...

Right on, I'll give it a shot tomorrow...I'm sure I'll get it working eventually. Hope it's worth the wait!

---

### Post by bkratz on 2012-04-24
> **Johnny Vox said:**
> Right on, I'll give it a shot tomorrow...I'm sure I'll get it working eventually. Hope it's worth the wait!



Johnny,

The information you received earlier was close (post 7) , but since you have the low power version of the 4312 (it is not close to the 4311)

0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g [COLOR=Red]LP-PHY[/COLOR] (rev 01)
	

you actually need to substitute 

firmware-b43-lpphy-installer


for the second step rather than the shown

firmware-b43-installer
Good luck.

---

### Post by Johnny Vox on 2012-04-24
> **bkratz said:**
> Johnny,

The information you received earlier was close (post 7) , but since you have the low power version of the 4312 (it is not close to the 4311)

0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g [COLOR=Red]LP-PHY[/COLOR] (rev 01)
    

you actually need to substitute 

firmware-b43-lpphy-installer


for the second step rather than the shown

firmware-b43-installer
Good luck.

Well the good news is, it is working on a wired connection at work. The bad news is, when I do the "get update command" I get another error:

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

---

### Post by ahallubuntu on 2012-04-24
The lock usually means you have another package tool open.  Make sure you close the Ubuntu Software Center and/or the Update Manager if they have opened.  Update Manager may open itself automatically to get you to do the updates as soon as you've connected the network cable.

In fact, close everything except the terminal you are typing the commands in.  And please use the command bkratz suggested instead of the one I originally gave you.

---

### Post by Johnny Vox on 2012-04-24
> **ahallubuntu said:**
> The lock usually means you have another package tool open.  Make sure you close the Ubuntu Software Center and/or the Update Manager if they have opened.  Update Manager may open itself automatically to get you to do the updates as soon as you've connected the network cable.

In fact, close everything except the terminal you are typing the commands in.  And please use the command bkratz suggested instead of the one I originally gave you.

Yes! Finally got it working, thank you guys so much for your help! MUCH appreciated!

---

### Post by ph4nt0m117 on 2012-04-24
Install the madwifi driver.

If it doesn't work with THAT, then there really isn't any help.

---

### Post by ahallubuntu on 2012-04-24
> **Johnny Vox said:**
> Yes! Finally got it working, thank you guys so much for your help! MUCH appreciated!

Glad to hear that.  Sorry to hear it was such a rude introduction to Ubuntu for you!  I've been using Ubuntu since 2005 in some form and full time on my laptop for a few years.  I love it.

---

### Post by bkratz on 2012-04-24
> **Johnny Vox said:**
> Yes! Finally got it working, thank you guys so much for your help! MUCH appreciated!


Glad you got it too!  Congratulations and enjoy!



By the way, please go to the thread tools above and mark as [solved] in case it helps someone else.

---

### Post by Johnny Vox on 2012-04-25
> **ahallubuntu said:**
> Glad to hear that.  Sorry to hear it was such a rude introduction to Ubuntu for you!  I've been using Ubuntu since 2005 in some form and full time on my laptop for a few years.  I love it.

Can you guys by chance direct me to a tutorial on sharing files between Windows and Ubuntu on the same pc? I'm having trouble finding straightforward info on that as well. Thanks!

---

### Post by ahallubuntu on 2012-04-25
You mean you want to dual boot Windows and Ubuntu but access the same files on that hard drive whether you are booted into Windows or Ubuntu?

I have found NTFS, the Windows file system, very reliable to use in Ubuntu.  So, you can either make your Windows partition really large and store most of your data on it and a small partition for Ubuntu, or you can make three partitions - small Windows 7 partition, small Ubuntu partition, and a larger data partition (which is how I've done it).  I've never had an issue accessing Windows NTFS data with the newer versions of Ubuntu.  I even have my NTFS partition encrypted with Truecrypt and still use it with Windows and Ubuntu.

I don't use the newest Ubuntu with the Unity that I think you are using, so I'm not familiar with the exact terminology of what you actually click on - but in the older versions of Ubuntu, you can just choose your Windows partition from the Places menu.  You can navigate to it to mount it in Unity pretty easily too I'm sure.

Like this:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

In that example, the Windows partition has no label so it shows up as "125 GB" and gets mounted with /media/32ablahblahblah .  You can go and add a label to it to give it a meaningful name - I named my data drive "DATA" so that's what I see in my menu.  To add a label like that (would still be C: in Windows), you can install gparted and add the label with that tool (a partition editor).

You can also automatically mount your Windows share upon boot by editing the /etc/fstab file in Ubuntu and adding your Windows partition to it.

---

