---
title: "[SOLVED] Adaptec 39160 prevents Ubuntu Boot"
date: 2008-09-09
forum: Hardware
---

### Post by lipinski on 2008-09-09
I have the following:
Dell Dimension 4500 running Ubuntu 8.04 Desktop.

I have an IDE drive (~40G, I think) attached to the IDE interface of the MB.  Ubuntu 8.04 Desktop installed without issue and has been running great.

I am going to be adding some SCSI drives to this unit, so I decided to install an Adaptec 39160 controller.  I installed the card in one of the empty 32-bit PCI slots (note: this is a 64-bit card, but is supposed to be compatible with 32-bit).  I did not attach any SCSI devices to this card at this time.

Immediately after installing this card, I booted up my system and everything was fine.  (I didn't notice any problems).

The next day, when I booted up my system, it wouldn't boot.  Well, specifically, it sends me to the initramfs prompt because GRUB complains that it cannot find my root device (via UUID).  I have tried to manually get grub to recognize my root device (/dev/sda6) to no avail.  In the initramfs prompt, I notice no /dev/sda devices exist initially.

I removed the SCSI card, and the system booted fine.

I installed the SCSI card again, and same problem.

As best I can tell, the kernel is stuck scanning SCSI devices and times out or something...  After waiting a long time in initramfs, I notice that my devices eventually end up under /dev (i.e., /dev/sda6, /dev/sda1, etc.).

My guess is that the aic7xxx driver is holding up the kernel in scanning for SCSI devices that grub times out or something...

Any ideas?  Let me know what info I can provide that would be more helpful....

---

### Post by lipinski on 2008-09-10
Well, after a lot of troubleshooting and trying different things on both the SCSI Adapter (Adaptec 39160), as well as passing options to aic7xxx during boot, modprobe, etc., I finially figured out a solution...

Believe it or not, just adding a device to the Adapter solved the problem.  I have no idea why this Adapter was insistent on scanning every SCSI ID during boot thus holding up the kernel to the point where my IDE boot/root drive was unavailable to grub...  

In any case, hope this helps someone.

---

### Post by stevetc on 2008-11-09
Hi,

i have the same problem.

I have installed Ubuntu 8.10 64bit Desktop-Version on a double Xeon Server with a Apaptec Scsi-Controler and it seems that the scsi-controller (aic79xx) makes some trouble.

I started from the live-cd and everything worked fine even the installation.
The boot messages show that he finds my hd like sda1 sda2... and sdb1 ...
But after a while the boot process stops and says "cannot find root".

In my case there are two harddisks attached to the scsi controller and i try to boot from a primary partition on the second disk.

Do you know a workaround ?

thanks Steve

---

### Post by kleeman on 2008-11-09
I have had this problem on two systems with scsi drives and reported it to launchpad

[https://bugs.launchpad.net/bugs/244608](https://bugs.launchpad.net/bugs/244608)

Please add your problems. My workaround was to use the hardy kernel (2.6.24-21) since I upgraded both systems from hardy

I also got a normal boot by typing exit at the busybox prompt

---

### Post by stevetc on 2008-11-11
I solved my problem simply adding 'rootdelay=130' in grub config, exactly at the end of the kernel parameter (/boot/grub/menu.lst)

---

### Post by kleeman on 2008-11-11
Great that worked for me on two systems. I will add the workaround to the bug entry

---

### Post by Mark Daniel on 2008-12-22
> **stevetc said:**
> I solved my problem simply adding 'rootdelay=130' in grub config, exactly at the end of the kernel parameter (/boot/grub/menu.lst)

I had this same problem, and was able to solve it by going into the adapter's BIOS management interface and (forgive me, I'm not in front of the machine!) changing each ID's setting for each adapter interface to be "multi-LUN friendly."

I can't state exactly what the setting was called, but the moment I saw it on-screen I knew I was onto something... and "multi-LUN friendly" would characterize the settings actual title well. ;)

---

### Post by hdmyg228 on 2009-01-08
This clock projects the time, date, or temp on the wall or ceiling [http://www.liangdianup.com/clocks_1.htm](http://www.liangdianup.com/clocks_1.htm)  some people call
it a ceiling clock but I call it a digital projection clock. I got the black one because at the time that was the only color
they had. But now they have them in black and also in white.

---

