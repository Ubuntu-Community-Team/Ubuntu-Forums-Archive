---
title: "Problems with a no CD, no floppy install"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by MattatHazmat on 2008-12-22
I'm trying to install Ubuntu on my Fujitsu Stylistic 3400.  It has no internal CD, and a single USB port without the ability to boot via USB (CD, or flash drive, and I'm not sure if I'll be able to use a floppy).  I've tried to follow the instructions [elsewhere here on ubuntuforums]("http://ubuntuforums.org/showthread.php?t=244918"), but I haven't had any luck, since I'm getting problems loading the FreeDOS floppy (I'm using WinImage and a USB floppy, and Winimage is giving errors).  I bought a USB floppy and USB drive to load from, but I haven't had much luck.  I don't have easy access to a machine that has a traditionally connected floppy, though I have XP, Vista, and Linux machines available that I can connect the USB floppy to.

I do have a working Linux server from which I was hoping to be able to load the relevant portions onto a hard-drive (via USB->IDE converter), but I'm not having any luck loading the MBR.  I've been able to create the partitions and load an .iso onto the drive, but no luck following other online tutorials on loading the MBR, so the tablet has something to boot from.  I'm just not sure what to try next.

This machine is able to boot windows from a the hard-drive that came from it, but I pulled that from the tablet so I have something to fall back on in case I screw up.  I'm not looking for a dual boot machine- this machine will only be running Linux.  My google searches have had some pretty promising returns, but I keep running into roadblocks, stopping my progress.

Ideally, I want this: a method to write the installation files to a clean hard drive from a working Linux or windows machine.  I'll remove the drive from that machine and then install it in the tablet, and from there I can boot the tablet and then install the OS for the tablet. Any help is appreciated, and will earn the frosty beverage of your choice, from me, if you are in or travel to the Austin, TX area.

Regards,

Matt

---

### Post by logos34 on 2008-12-22
> **MattatHazmat said:**
> I do have a working Linux server from which I was hoping to be able to load the relevant portions onto a hard-drive (via USB->IDE converter), but I'm not having any luck loading the MBR.  I've been able to create the partitions and load an .iso onto the drive, but no luck following other online tutorials on loading the MBR, so the tablet has something to boot from.  I'm just not sure what to try next.


You're close--Give this method a shot:

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

### Post by MattatHazmat on 2008-12-28
> **logos34 said:**
> You're close--Give this method a shot:

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

That's a start, but that page, well, um... definitely needs updating.  One of those pages you really need to read the whole thing, a couple times, before you start to act!  As I read it, it transitions from installing onto a separate drive to just installing on the main drive of the system (as I understand it)- I definitely don't want to overwrite the boot sector on my server.

The place I'm confused now is how to run grub on the USB connected hard-drive.  When I do a 'grub-install /dev/sdc' I get a message that '/dev/sdc does not have any corresponding BIOS drive'- which sounds right, since it is a USB drive, but I still want to install to it anyway.

I did find this [http://ubuntuforums.org/showthread.php?t=245690](http://ubuntuforums.org/showthread.php?t=245690) about using dd to copy the boot sector from my current drive over- and something happens now- when I put that drive into the tablet, it boots and I get a 'GRUB' on the screen, but nothing more.  I'm a bit confused as to how to set up grub on this drive.  From what I understand, I'm getting into grub, but grub doesn't know what to do next.  I'm trying 'procedure 2' from the first link quoted above, but I'm not sure where to put the grub.conf file.  I have a feeling that doing the dd method is a bit riskier and somewhat of a brute force way to do it. 

Any additional pointers, particularly on grub, would be helpful.

---

### Post by maybeway36 on 2008-12-28
Here's what I do from a working Linux system:
1. download "linux" and "initrd.gz" from [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/ubuntu-installer/i386/](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/ubuntu-installer/i386/). Save them to your home directory.
2. Edit /boot/grub/menu.lst. Add:
```
title Ubuntu 8.10 install
root (put your root partition here)
kernel /home/[username]/linux vga=normal
initrd /home/[username]/initrd.gz
```
3. Reboot and try loading it. If it works, install!

As you can see, I like doing it manually. UNetbootin pretty much does this for you.

---

### Post by logos34 on 2008-12-28
> **MattatHazmat said:**
> 
The place I'm confused now is how to run grub on the USB connected hard-drive.  When I do a 'grub-install /dev/sdc' I get a message that '/dev/sdc does not have any corresponding BIOS drive'- which sounds right, since it is a USB drive, but I still want to install to it anyway.

I did find this [http://ubuntuforums.org/showthread.php?t=245690](http://ubuntuforums.org/showthread.php?t=245690)... 

...

Any additional pointers, particularly on grub, would be helpful.

The dd command in that link is wrong (should be bs=512 count=1)...besides, you need the grub files.

Try making a dedicated grub partition [as described here]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_"), then copy /boot/grub files (from server) to it, edit menu.lst to include boot entry for ubutnu live iso, and install grub stage1 to the mbr.  

Either that or use [GAG bootloader]("http://gag.sourceforge.net/").  Doesn't even need it's own partition--installs to the first sector of the hard disk.

---

### Post by plarq on 2008-12-29
> **maybeway36 said:**
> Here's what I do from a working Linux system:
1. download "linux" and "initrd.gz" from [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/ubuntu-installer/i386/](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/ubuntu-installer/i386/). Save them to your home directory.
2. Edit /boot/grub/menu.lst. Add:
```
title Ubuntu 8.10 install
root (put your root partition here)
kernel /home/[username]/linux vga=normal
initrd /home/[username]/initrd.gz
```
3. Reboot and try loading it. If it works, install!

As you can see, I like doing it manually. UNetbootin pretty much does this for you.

GRUB now uses "linux" instead of "kernel". New GRUB also start from (hd0,1) as /dev/sda1

So it was linux /home/.../vmlinuz
initrd /home/.../initrd.gz,  as a entrymenu.

My problem is when I boot from an iso file or a hard disk partition with content of Live CD, it gives me a live session like booting from Live CD, but I can't install because the partition phase of installation shows me nothing and I can't go on. Booting from old live cd gives me choice between partitions.

---

### Post by logos34 on 2008-12-29
> **plarq said:**
> can't install because the partition phase of installation shows me nothing and I can't go on. Booting from old live cd gives me choice between partitions.

What about exiting the install session, going back to the live desktop and opening Gparted (System>admin>partition editor.  Does gparted see the disk/partitions?

---

### Post by MattatHazmat on 2008-12-29
> **logos34 said:**
> 
Try making a dedicated grub partition [as described here]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_"), then copy /boot/grub files (from server) to it, edit menu.lst to include boot entry for ubutnu live iso, and install grub stage1 to the mbr.  

Either that or use [GAG bootloader]("http://gag.sourceforge.net/").  Doesn't even need it's own partition--installs to the first sector of the hard disk.

Argh! I'm not having any luck- I'm just getting a flashing cursor- no messages... nothing else.  I've installed the grub partition as you suggested, but no luch.  I may try GAG, but that will have to wait until tomorrow- It's late, and I'm tired.

Is there any way to have grub write a log file of what it has done?  I can pull the drive out and check if grub has written any diagnostics, if it has that ability.

Once I install grub, I just need to edit the grub.conf file, correct?  I shouldn't have to re-run grub grub shell and do all the stuff related to that, correct?

---

### Post by plarq on 2008-12-29
> **logos34 said:**
> What about exiting the install session, going back to the live desktop and opening Gparted (System>admin>partition editor.  Does gparted see the disk/partitions?

Yes, gparted of Live Session works fine.

---

### Post by logos34 on 2008-12-29
> **MattatHazmat said:**
> 
Once I install grub, I just need to edit the grub.conf file, correct?  I shouldn't have to re-run grub grub shell and do all the stuff related to that, correct?

not sure about the grub error log

the fact that you're doing this on the hdd with it attached to the other machine is not making things any easier--when you write grub to the mbr maybe it's throwing off the location so that when you plug it back into the fujitsu it can't find the menu.lst on the dedicated grub partition. 

You don't need to re-run grub shell after editing menu.lst.  

wish I could help more

---

### Post by MattatHazmat on 2008-12-30
> **logos34 said:**
> not sure about the grub error log

[...]

wish I could help more

Thank you for your help- I'll keep monitoring the thread- if anyone has ideas, I'll be happy to try 'em out.  Otherwise, I'll put this into the 'cold case' file of projects to work on another day...

Regards.

---

### Post by MattatHazmat on 2009-02-04
Have the first hurdle jumped- I took the hard drive out and put it into another laptop that can do a CD-ROM based install (A Dell Inspiron 8500), did the install, and pulled the drive out of the Dell and put it into the Tablet.  Now I have Ubuntu 8.10 on the tablet.  Now I've got all sorts of setting up to do to get the touch screen working (which I've seen elsewhere on this forum).  Again, a work in progress.

---

