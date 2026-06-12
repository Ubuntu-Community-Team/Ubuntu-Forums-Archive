---
title: "Machine locks hard when trying to eject cdroms"
date: 2004-12-08
forum: Hardware &amp; Laptops
---

### Post by scp on 2004-12-08
Greetings, 

I have an Intel machine with 2 IDE cdrom drives in it (1 reader and 1 reader/writer) . For the last couple of days I have noticed a peculiar problem. When I try to eject my empty cd burner (using the button on the front of the unit)  it is "locked" (the behavior you normally see when it is mounted.) Then, about a minute or so later, the machine hangs hard and the hard disk activity light on my machine stays on solid. Anyone have any ideas? The machine had been up for only 24hrs because I encountered the same problem yesterday. The machine becomes completely unresponsive to the console, and cannot be accesed remotely via ssh. I have posted information/logs below. Also note, I noticed that have had a data cdrom in the first drive (the reader, not the one that I was trying to eject) during this whole time, but it has not been mounted.

Any help is greatly appreciated, thanks in advance.

Here's how my IDE disks are connected:
==============================================
    ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda: DMA, hdb: DMA
    ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc: DMA, hdd: DMA

Disk information:
==============================================
hda: MAXTOR 6L040J2, ATA DISK drive
hdb: ST3200822A, ATA DISK drive
hdc: Lite-On LTN486S 48x Max, ATAPI CD/DVD-ROM drive
hdd: SAMSUNG CD-R/RW SW-252S, ATAPI CD/DVD-ROM drive

logs from /var/log/syslog at time just before crash (appears to be just as I was hitting the cdrom eject button):
==============================================
Dec  8 23:11:12 localhost kernel: hdd: irq timeout: status=0xd0 { Busy }
Dec  8 23:11:12 localhost kernel: hdd: irq timeout: error=0x00
Dec  8 23:11:12 localhost kernel: hdd: DMA disabled
Dec  8 23:11:42 localhost kernel: hdd: ATAPI reset timed-out, status=0x80
Dec  8 23:11:42 localhost kernel: hdc: DMA disabled
Dec  8 23:12:17 localhost kernel: ide1: reset timed-out, status=0x80
Dec  8 23:12:17 localhost kernel: hdd: status timeout: status=0x80 { Busy }
Dec  8 23:12:17 localhost kernel: hdd: status timeout: error=0x01IllegalLengthIndication
Dec  8 23:12:17 localhost kernel: hdd: drive not ready for command
Dec  8 23:12:47 localhost kernel: hdd: ATAPI reset timed-out, status=0x80

Kernel Information:
==============================================
Linux silvertree 2.6.8.1-3-686 #1 Thu Nov 18 12:19:06 UTC 2004 i686 GNU/Linux

---

### Post by scp on 2004-12-09
*** UPDATE ***

After my last crash/reboot, I removed the disc (the one that I never had mounted) from the first drive (the reader) and I have had no issues since then. The cdroms function as expected now.

Should I submit a bug report? Of course, I would make sure that I can get this to happen consistantly before I did such a thing. Which will probably take a couple of days and some patience. :wink: ...

If this is in fact something that is re-producable, I want to actively participate in making sure this gets resolved. It is rather annoying and I am sure someone else will feel the pain if it does not get fixed.  :-D

---

### Post by anselm on 2004-12-23
I am having the same problem, I have only one cdrom hooked up and it is a SAMSUNG CD-R/RW SW-252S, I tried to open the cdrom by pressing the button and nothing happened than the system froze up hard had to do a cold reboot once I rebooted the cdrom worked fine, I leave the system running 24/7 so I don't know when this actually first happens.

Thanks

---

### Post by scp on 2004-12-23
Does this happen when you have a CD in the drive? I find that if there is not a CD in my first drive, I have no problems. I have tried several times to re-create, and it only happens when there is a CD in my first drive that is not mounted (the machine booted up with it in the drive and it was never mounted.) So what I have been doing is making sure that my drives stay empty when not in use, and I haven't had any problems since.  I also have put a "pci=noacpi noapic" on my kernel boot line per directions from someone in #ubuntu-devel , this may also be helping.

---

### Post by anselm on 2004-12-23
It happens wether I have a cd in the drive or not it just locked up right now when I was getting ready to replay to this post.

Where do you add that line in the kernel boot line??

Thanks

---

### Post by scp on 2004-12-23
You can add it in /boot/grub/menu.lst on the "kernel" line. You pass it to the "command-line" of the kernel. NOTE: The documentation I have seen for the noapic option say it's for SMP kernels (see: kernel-parameters.txt in kernel source tree,) but I was told to use it and I am on a single processor system. 

Here are some references:
[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)
[http://www.gnu.org/software/grub/manual/grub.html#kernel](http://www.gnu.org/software/grub/manual/grub.html#kernel)

---

### Post by Levander on 2005-03-31
Did you guys every figure out this issue?  I posted about a similar problem a few days ago in a new thread, nobody responded.

I've got very similar messages mentioned in the first post in this thread just flat out filling up syslog hour by hour.

---

### Post by liuter2045 on 2007-05-15
Re: Machine locks hard when trying to eject cdroms
[memory insects build Girls Debt Consolidation](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/incest-porn.html)

---

### Post by EugeniuV495 on 2007-05-15
> **scp said:**
> Does this happen when you have a CD in the drive? I find that if there is not a CD in my first drive, I have no problems. I have tried several times to re-create, and it only happens when there is a CD in my first drive that is not mounted (the machine booted up with it in the drive and it was never mounted.) So what I have been doing is making sure that my drives stay empty when not in use, and I haven't had any problems since.  I also have put a &quot;pci=noacpi noapic&quot; on my kernel boot line per directions from someone in #ubuntu-devel , this may also be helping.


[solar American Idol Google Debt Consolidation Paris Hilton](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/latin-porn.html)

---

