---
title: "Lightscribe Drives"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by J-Red on 2007-07-01
I finally got past the xorg errors I was having with my computer, and everything seems to work fine except for the CD/DVD drive. The laptop that I am currently using is a HP Compaq 6710b, and I'm not sure the exact model of the built in drive, but I know that it is a Lightscribe drive. I downloaded some .rpm from the lightscribe website, and converted them to .deb with alien. The drivers aren't meant for Ubuntu, and ubuntu isn't officially supported yet, but there must be some way to get it working. Does anyone have the same drive or have any ideas on how I can make the drive work?

---

### Post by zzak on 2007-07-01
What happens when you install a CD ?
Do you get a window with the contents ?
 If not, try mounting it as root.  If your partitions are shown as /dev/sdax,  then the drive will be  /dev/hda.

---

### Post by yorkie on 2007-07-01
Go into Synaptic Package Manager search for lightscribe two items to install
4l 1.01
lightscribe 1.4.136.11
When installed open a terminal type  gksudo 4L-gui
This should work

---

### Post by J-Red on 2007-07-01
I already have the packages installed, and it still doesn't seem to work.


 When I try to go to the "CD-ROM 1" from nautilus, it tells me that it is unable to mount the selected volume, it also says "mount: special device /dev/hda does not exist".

---

### Post by yorkie on 2007-07-01
Cd/Dvd drives are normaly mounted in /Media folder
IN fstab file Ihave the following lines
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
 I f you arenew to linux fstab is in /etc folder
hope this helps

---

### Post by PilotJLR on 2007-07-01
Just pop a CD in the drive and see if an icon is placed on your desktop... or if a window pops up.

Forget about the lightscribe rpm files for now... those provide labelling functionality, but have nothing at ALL to do with data discs.

---

### Post by J-Red on 2007-07-01
I have tried disks, its not in the media folder.

It seems as if the laptop is not recognizing the drive at all, that is why I installed the software, I didn't know thats only for labling. I'm pretty sure the laptop isn't even recognizing the drive as existing.

---

### Post by PilotJLR on 2007-07-01
Let's try this then... please put a CD-ROM in the drive, and then open a terminal.
The following commands will manually mount the CD:
```

sudo mkdir /mnt/cd
sudo mount /dev/cdrom /mnt/cd
ls /mnt/cd

```

If that works... and if the list command produces valid output, then we know the drive is detected properly. If this fails, then the please paste the output of:
```

lspci

```

---

### Post by J-Red on 2007-07-01
Error that I got while trying to manually mount:
> mount: special device /dev/cdrom does not exist


lspci gives me:
> 
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 03)
02:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)
02:04.1 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 02)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
18:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)


When looking through that, I couldn't seem to even find the drive.

---

### Post by geraldm on 2007-07-01
use command dmesg or file /var/log/dmesg to identify failure to find the drive.
It should contain a message as to why.

---

### Post by J-Red on 2007-07-02
That gave me a really long output, so I just threw it into pastebin instead of posting here:
[http://ubuntu.pastebin.com/940352](http://ubuntu.pastebin.com/940352)

Can anyone help me with finding out the error? I'm not very good with Linux right now, and I'm still learning.

---

### Post by J-Red on 2007-07-02
*bump*

---

### Post by rkrastev on 2007-07-03
Hi,

I have the same laptop (HP 6710b) and the same problem. K3B says that I don't have DVD writer.

Please help.

rkrastev

---

### Post by J-Red on 2007-07-05
it says that /dev/hda doesn't exist. Is there any chance that Ubuntu put the drive in some other location? If so, how do I find out?

---

### Post by J-Red on 2007-07-06
re-bump...

Does anyone have any idea what I could do? I've talked to someone who has the same laptop, or maybe a bit of a better version of it, and they said that the drive worked automatically.... Can anyone help me with this??

---

### Post by Extreme Coder on 2007-07-09
After reading the thread, I have no idea what's causing this problem.
I'd suggest trying a different distro of Linux, to see where the problem is.
Why not try Mandriva One?

---

### Post by wistof on 2007-07-10
Hi,

I have a 6710b too, and i have need to load 'ide-generic' module for make my dvd work.

The relevant part of my dmesg :

```
[  740.312000] Probing IDE interface ide0...
[  741.180000] hda: HL-DT-ST DVDRAM GSA-T10N, ATAPI CD/DVD-ROM drive
[  741.516000] Probing IDE interface ide2...
[  742.076000] Probing IDE interface ide3...
[  742.636000] Probing IDE interface ide4...
[  743.196000] Probing IDE interface ide5...
[  743.756000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[  743.824000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[  743.824000] Uniform CD-ROM driver Revision: 3.20

```

And i erase successfully  a DVD-RW with gnomebaker. 
I hope that can help you

---

### Post by wistof on 2007-07-10
> **wistof said:**
> Hi,

I have a 6710b too, and i have need to load 'ide-generic' module for make my dvd work.

The relevant part of my dmesg :

```
[  740.312000] Probing IDE interface ide0...
[  741.180000] hda: HL-DT-ST DVDRAM GSA-T10N, ATAPI CD/DVD-ROM drive
[  741.516000] Probing IDE interface ide2...
[  742.076000] Probing IDE interface ide3...
[  742.636000] Probing IDE interface ide4...
[  743.196000] Probing IDE interface ide5...
[  743.756000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[  743.824000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[  743.824000] Uniform CD-ROM driver Revision: 3.20

```

And i erase successfully  a DVD-RW with gnomebaker. 
I hope that can help you

I've find a better way here => [http://blaise.ca/blog/?p=14](http://blaise.ca/blog/?p=14)

just load 'piix' 
```
sudo modprobe piix
```

---

