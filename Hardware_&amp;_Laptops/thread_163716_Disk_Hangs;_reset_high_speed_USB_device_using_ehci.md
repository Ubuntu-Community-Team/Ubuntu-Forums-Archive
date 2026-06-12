---
title: "Disk Hangs; reset high speed USB device using ehci_hcd and address 2"
date: 2006-04-21
forum: Hardware &amp; Laptops
---

### Post by ubusarah on 2006-04-21
Hi,

I have Breezy Badger installed and working fine... except...

I have /home and /usr/local mounted to an external 2.5" bus-powered USB Drive, both filesystems are formatted as ext3, and I am *not* trying to hot plug the drive. Usually, this setup works just fine. 

However, a couple times a day, as I'm working with it, periodically the whole machine just seems to "lock up" for a little while, oh, maybe 10-30 seconds. By fiddling, examining logs, and watching carefully, I was able to discover that apparently what happens is that disk access will hang for a little while, and then finally, the message:

     usb 3-1: reset high speed USB device using ehci_hcd and address 2

gets written into /var/log/kern.log, and then everything goes back to normal. Until it happens again.

What's going on? Should I be worried? Can I fix this? Hardware problem? Software problem? Bug?

I'm thinking about switching from the little laptop drive to an IDE drive caddy to get rid of this problem, but it's not my first choice.

Oh, and I mostly access this machine remotely using MacOS X X11 and gig ethernet. The box itself is a Shuttle SS56GV2 with a 2.8gig celeron and 2gig ram, with two internal IDE drives that hold everything except /home and /usr/local. No USB hub. iptables is configured for a very tight firewall.

Thanks,

Sarah

---

### Post by z_diver on 2006-04-21
[QUOTE=ubusarah]
I have /home and /usr/local mounted to an external 2.5" bus-powered USB Drive, both filesystems are formatted as ext3, and I am *not* trying to hot plug the drive. Usually, this setup works just fine. [/QUOTE]

By bus-powered do you mean it's plugged into usb for I/O transactions and ps2 for power?  :-k 

I have a collection of these devices and I've never been able to get them to work properly.  I don't know what it is about them but I have had much better luck using firewire(on Mac) and ac/dc powered usb enclosures with on/off switches for Linux/Win/Mac.

---

### Post by ubusarah on 2006-04-21
[QUOTE=z_diver]By bus-powered do you mean it's plugged into usb for I/O transactions and ps2 for power?  :-k 

I have a collection of these devices and I've never been able to get them to work properly.  I don't know what it is about them but I have had much better luck using firewire(on Mac) and ac/dc powered usb enclosures with on/off switches for Linux/Win/Mac.[/QUOTE]

No, I mean powered entirely from the USB bus. Which is why I don't, for instance, have them plugged into a passive hub. Not enough power.

There's clearly enough power for it to work... and these particular enclosures have been reliable for me in the past, plugged into other hardware, but... hmm... I wonder if, for instance, the drive is being spun down, and when it spins back up it doesn't *quite* have enough power? The transient voltage drop might cause the drive controller to reset which would confuse the driver, which would eventually time out... and issue a reset? It could also be that the ports on the Shuttle box don't provide quite as much power as my other hardware does.

It might also have to do with the drive in the enclosure being a somewhat older drive. It probably consumes a bit more power than a more modern one.

Hmm, yes, you might be right. It could be a power issue. I'll fiddle with it when I get a chance. I do have some external firewire enclosures that use AC power; I could use one of those instead.

---

### Post by fritztcat on 2007-08-03
Even if this thread is a bit dated by now, I post what worked for me to solve this problem with feisty:

The max_sector was set too high for the usb harddisk. 

```
cat /sys/block/sda/device/max_sectors
```

reported 240 sectors (assuming the usbdisk is /dev/sda). Setting it to 128 with

```
echo 128 >/sys/block/sda/device/max_sectors
```

did the trick for me, as this is the maximum number of sectors the hdd can read/write at once. For some drives the optimal value could be 64.

- Fritz

---

### Post by cberthe on 2007-09-09
I exactly have the same problem using Mac OS X to access shared USB discs on my ubuntu ... 
Reducing the max_sectors to 64 do not solve the problem for me ...

This problem only occurs with Mac OS X accessing samba shares ...

I do not understand why ...

Does anyone have a solution to this problem ?

Thank you !

---

### Post by Nephiel on 2008-01-24
I have exactly the same problem.
dmesg says this:
```
[43385993.110000] usb 4-6: new high speed USB device using ehci_hcd and address 7
[43385993.260000] scsi4 : SCSI emulation for USB Mass Storage devices
[43385993.260000] usb-storage: device found at 7
[43385993.260000] usb-storage: waiting for device to settle before scanning
[43385998.260000]   Vendor: SanDisk   Model: U3 Cruzer Micro   Rev: 4.05
[43385998.260000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[43385998.260000] SCSI device sda: 8027789 512-byte hdwr sectors (4110 MB)
[43385998.260000] sda: Write Protect is off
[43385998.260000] sda: Mode Sense: 03 00 00 00
[43385998.260000] sda: assuming drive cache: write through
[43385998.270000] SCSI device sda: 8027789 512-byte hdwr sectors (4110 MB)
[43385998.270000] sda: Write Protect is off
[43385998.270000] sda: Mode Sense: 03 00 00 00
[43385998.270000] sda: assuming drive cache: write through
[43385998.270000]  sda: sda1
[43385998.270000] sd 4:0:0:0: Attached scsi removable disk sda
[43385998.270000] sd 4:0:0:0: Attached scsi generic sg0 type 0
[43385998.270000] usb-storage: device scan complete
```
After reading files from the disk for a few seconds, the disk hangs and these lines pop up in dmesg:
```

[43386170.030000] usb 4-6: reset high speed USB device using ehci_hcd and address 7
[43386171.150000] usb 4-6: device descriptor read/64, error -71

```

I'm using Ubuntu 6.06 Server (LTS) with the latest kernel and updates.
The USB disk is a 4GB Sandisk Cruzer Micro that works fine under Windows.

Is there something I could do?

---

### Post by fsu8 on 2008-03-09
Try this:

modprobe -r ehci_hcd

My laptop works after this. It then uses uhci_hcd driver which is USB1.0 speed (very slow). A post ([http://lists.debian.org/debian-amd64/2004/12/msg00139.html](http://lists.debian.org/debian-amd64/2004/12/msg00139.html)) said this:

"Try a different cable. If the UHCI controller can operate the device, but the EHCI controller cannot, you either have a broken kernel build (unlikely) or the electrical connection cannot maintain the 480 megabit performance. "

Either it's a power/hardware issue or a bug in ehci_hcd.

---

### Post by Nephiel on 2008-03-14
Still having this problem after updating to the latest Dapper LTS kernel (2.6.15-51-386-i686). It's really frustrating.

Happens on both my desktop and my laptop, with different USB mass storage devices (a Sandisk Cruzer Micro 4GB, a Iomega 3.5" enclosure with external power supply, a Conceptronic 3.5" enclosure also with external power, and even an iPod in disk mode). All of these devices work fine under Windows on my laptop.

Unloading ehci_hcd works, but USB 1 is too slow for large transfers of files (backups and syncs).

Tried different PCI-to-USB adapter cards on my desktop PC, with different chipsets (VIA and Ali) and neither worked well.

Also tried disabling the athcool daemon on my desktop PC, just in case. Still no luck.

Bad wiring? The Sandisk Cruzer plugged directly into the rear USB ports of the motherboard also has this problem. And the iPod is using the bundled cable, which works fine (and fast) under Windows.
Power issue? I don't think so; both of the hard drive enclosures I've used have external power supplies, and the same thing happens to them.

It seems this bug has been around for quite a while. I've seen lots of web pages, forum posts and bug reports about what seems to be the same issue, and no solution yet :(

---

### Post by Nephiel on 2008-03-30
Seems to be related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746)

No solution yet :frown:

---

### Post by CrazyGuy123 on 2008-04-23
this is a 2+ year old bug, which still happens in the latest hardy release candidate.

It should have higher priority, as really it is a blocker to using ubuntu in some situations.

In case you need another test case, it also occurs with a 4GB "Super-Talent" USB2.0 flash disk on an hp nx6125 laptop.  Changing bios usb settings has no effect.  I don't have the experience or equipment required to start debugging usb bus problems.

---

### Post by PVi1 on 2008-05-08
Hello,

I have similar problem with Microsoft Natural Ergonomic Desktop 7000.
I am using Ubuntu 8.04LTS.

Every few seconds keyboard&mouse get frozen, or keyboard types Xtimes last pressed character.

I can see a lot of these this entries in syslog:

[ 7169.642329] usb 3-4.3: reset low speed USB device using ehci_hcd and address 5
[ 7179.160951] usb 3-4.3: reset low speed USB device using ehci_hcd and address 5
[ 7179.712555] usb 3-4.3: reset low speed USB device using ehci_hcd and address 5

I have keyboard receiver connected to my docking station and Ubuntu detect this device as USB hub.

Peter

---

### Post by Moldavit on 2008-06-13
I observe the same USB 2.0 failure mode under "Hardy" Ubuntu 8.04 LTS:

        reset high speed USB device using ehci_hcd

ajisai:~$ uname -a
Linux ajisai 2.6.24-18-server #1 SMP Wed May 28 20:21:05 UTC 2008 x86_64 GNU/Linux

Hardware is SUPERMICRO PDSG4 motherboard with ASUS 7600GS graphics card.

Failure occurs for all of:
        2 Gb Memorex TravelDrive
        250 Gb Western Digital Passport WD2500XMS
        750 Gb Seagate 3.5" External ST3750640CB-RK

---

