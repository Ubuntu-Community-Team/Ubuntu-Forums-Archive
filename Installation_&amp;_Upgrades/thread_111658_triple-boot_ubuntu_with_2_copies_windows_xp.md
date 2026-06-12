---
title: "triple-boot ubuntu with 2 copies windows xp"
date: 2006-01-02
forum: Installation &amp; Upgrades
---

### Post by scotartt on 2006-01-02
Hello,

I am new to Ubuntu, although not to Linux overall. However in the past I have always done single-boot dedicated machines for Linux. 

I am trying to install Ubuntu on my Laptop's (Dell Inspiron 8500) external USB disk. The problem I am having is that this machine already has a dual-booted Windows XP environment on it - one a standard xp installation the other a completely cut-down XP environment for music work.

Thus, when I get to the 'installing grub' stage of the installation, I am extremely reluctant to allow grub to overwrite my MBR on the main hard disk. It reports there is a copy of Windows (boot ldr) on the MBR, but frankly as the Windows boot environment is very precious to me and I don't really want to spend a day recovering it (also I've only got the CD that will do a 'clean install' of Windows XP pro which also I don't want to do particularly on the second of the two Windows installations, as it takes ages to configue windows to "everything off").

I was wondering how safe it was to allow grub to install itself to the MBR. Will it allow me to boot my copy of Ubuntu, and ***both*** my existing copies of Windows? And what if the USB disk (where Ubuntu is installed to) is not plugged in at time of boot?

I have tried a number if alternatives, such as trying to install Grub to the USB disk and altering my BIOS settings so the machine is able to boot off USB devices, but either the computer can't actually do this or my grub installation to the USB disk is faulty as it won't boot from the USB disk after the installation process's reboot. I've also looked at some web pages which cover some of the ground but not, as yet, all of it that I need.

Any help or tips would be appreciated.

thanks
scot mcphee

---

### Post by Zelut on 2006-01-02
If your machine is capable of booting to USB have you tried running the live CD from the USB drive?  That may be an option...

---

### Post by scotartt on 2006-01-02
[QUOTE=kuyaedz]If your machine is capable of booting to USB have you tried running the live CD from the USB drive?  That may be an option...[/QUOTE]

No I have not tried that. How would I copy the live cd's ISO image to my USB hard disk such that it's bootable?

---

### Post by Zelut on 2006-01-02
[https://wiki.ubuntu.com/BootingFromUSB](https://wiki.ubuntu.com/BootingFromUSB)

take a look there & see if that helps you at all..  sounds like this might be your best solutions.  1) keeps your XP partitions intact.  2) will only boot to Ubuntu if/when your USB is attached. 3) you'll be able to keep/write files to your USB drive for future use...

---

### Post by limit223 on 2006-01-02
If you really understand my post:
[http://ubuntuforums.org/showpost.php?p=609948&postcount=20](http://ubuntuforums.org/showpost.php?p=609948&postcount=20)

 you'll be able to have backup/restore of your MBR,  rescuing anytime you get in trouble booting your fixed harddisk systems.

---

### Post by jjross on 2006-01-02
[http://www.ubuntuforums.org/showthread.php?t=56723](http://www.ubuntuforums.org/showthread.php?t=56723)
try looking at this link, i did this and it works great for me.
i have two versions of xp on my computer as well as ubuntu 5.10

---

### Post by limit223 on 2006-01-02
jjros, indicated a NT bootloader for all your systems, including linux one..
that's exactly what I use in booting my 5 systems: 2 windows, Slackware, Suse, Ubuntu...:)

---

### Post by scotartt on 2006-01-03
[QUOTE=jjross][http://www.ubuntuforums.org/showthread.php?t=56723](http://www.ubuntuforums.org/showthread.php?t=56723)
try looking at this link, i did this and it works great for me.
i have two versions of xp on my computer as well as ubuntu 5.10[/QUOTE]

I have been trying to do exactly that (use the nt loader as described) but as of yet, no success -- the copy made by dd doesn't boot properly, sometimes manages to output 'GRUB' but then locks up. there's also no floppy on this machine like most modern laptops.

thanks for all yr help I'm gonna persist and try a couple more times with some variations here or there. else maybe the inspiron just can't boot off usb.

---

### Post by scotartt on 2006-01-03
Well I've tried and tried to make the inspiron 8500 boot from the USB disk and it just doesn't seem to want to do it at all. I guess I'm just gonna give up on it until I can get the machine in the situation of replacing one of the windows installs completely.

---

### Post by scotartt on 2006-01-04
[QUOTE=scotartt]Well I've tried and tried to make the inspiron 8500 boot from the USB disk and it just doesn't seem to want to do it at all. I guess I'm just gonna give up on it until I can get the machine in the situation of replacing one of the windows installs completely.[/QUOTE]

I am just putting this here for the sake of completeness. I am now booted into my laptop-installed version of Ubuntu! 

Thanks for everyone who gave information.  The link [https://wiki.ubuntu.com/BootingFromUSB](https://wiki.ubuntu.com/BootingFromUSB) given by 'kuyaedz' seems about correct. For some reason the Dell Inspiron 8500 cannot boot from a USB hard disk. Perhaps some drivers are needed first.

A friend emailed me the following, which appears to sum up the situation I experienced:

> I dealt with the same issue a while back, only on Arch Linux.  Dunno if you know all this already or not, but it turned out the issue was that I needed to set up an initrd to load all the USB drivers before the kernel loaded or else I couldn't boot.  

In the end I did the following;

1. Copy my big data partition off the internal hard disk onto the USB disk

2.  Repartition the internal hard disk with Partition Magic to free some room for the  Ubuntu install.

3. Install Ubuntu to e.g /dev/hda7. *Do not make it the active partition*.

4. Do NOT allow grub to be installed to the MBR of /dev/hda. Install it to /dev/hda7 instead.

5. Reboot with the Ubuntu Live CD.

6. Using instructions similar to the one found here - [http://ubuntuforums.org/archive/index.php/t-80508.html](http://ubuntuforums.org/archive/index.php/t-80508.html) - or the link posted above by "jjross" ( [http://www.ubuntuforums.org/showthread.php?t=56723](http://www.ubuntuforums.org/showthread.php?t=56723) ), create an image that can be used to bootstrap the Grub installation on /dev/hda7 from the Windows XP Boot Loader. e.g. "dd if=/dev/hda7 of=ubuntu510.bin bs=512 count=1"

7. Copied the ubuntu.bin to a FAT-32 disk partition visible from Ubuntu and Windows XP.

8. Rebooted into my primary Windows XP installation (the one that boots from drive "C:"). Added the following line to the file [FONT="Courier New"]C:\boot.ini[/FONT] that's used by the Windows boot loader: [FONT="Courier New"]C:\ubuntu510.bin="Ubuntu Linux"[/FONT]

9. Rebooted machine, and from the Windows Boot Loader menu, selected the "Ubuntu Linux" operating system.

10. Configured Linux, and came here to write this up in case some one turns it up in a search.

I haven't yet tried to boot both copies of Windows XP on the laptop but neither should be affected. 

When I tried this procedure for an installation on the USB hard disk, it wouldn't boot, which points to some issue for the USB hard disk and booting off it, possibly related to what my friend wrote to me above. 

The only downside about this set up now is that I have to cart the portable hard disk around if I want to use all my music data. At first I wanted to put Ubuntu on the portable drive so that I could leave the disk behind when I wanted to get my portable studio on the road. Only a small inconvienience.

thanks again to all who helped or tried to help.

scot.

---

