---
title: "dual boot  -  boot.ini"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by maccom on 2005-12-09
Hi,
i DOS booted and ran "FDISK /MBR", to remove grub.
I am now trying to edit my boot.ini file to get it to boot windows xp pro (default) or ubuntu (hoary)
I run ubuntu on my slave hdd, with default partitioning of the install disk. I have attempted to guess how to add ubuntu, this is what i have so far:

[quote="boot.ini"][boot loader]
timeout=05
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP" /fastdetect
multi(0)disk(1)rdisk(0)partition(1)\GNOME="Ubuntu Linux "Hoary Hedgehog""[/quote]

If this is the problem why i cant boot into ubuntu please could someone correct it for me.

TIA
[MacCom.1.vg](MacCom.1.vg)

---

### Post by amohanty on 2005-12-09
[http://www.highlandsun.com/hyc/linuxboot.html](http://www.highlandsun.com/hyc/linuxboot.html)
NOTE: uses LILO not GRUB.
AM

---

### Post by maccom on 2005-12-10
I have just received my 5.10 CDs and am going to install this.
i will put lilo on and then can this tut be used for 5.10 aswell or is there something different i need?

---

### Post by maccom on 2005-12-10
Just installed 5.10 "breezy"   but as with installation of 5.04 i had an error with installing lilo it has error code "1"!?!?!

I have installed grub as my mbr, what do i need to do to make boot.ini boot into linux properly now?

please note: n00b, only been using linux for 6 hours!! (est. time of usage)

---

### Post by linbetwin on 2005-12-10
What does GRUB have to do with boot.ini? When you reboot doesn't GRUB offer you the choice between Windows and Ubuntu?

---

### Post by kairu0 on 2005-12-10
[QUOTE=maccom]
I have installed grub as my mbr, what do i need to do to make boot.ini boot into linux properly now?
[/QUOTE]

What will happen is your computer will boot, read the MBR on your first drive, and load the Windows boot loader. Once it gets this far, it doesn't matter what the MBR on your slave drive is; it only cares about the partitions.

If you want to use Windows' boot.ini to dual boot between the two, then I would suggest that you install grub on the partition instead of on the MBR. Then, set up boot.ini (I think the configuration that you posted earlier will work.

P.S. Use GRUB, not LILO.

---

### Post by maccom on 2005-12-10
thanks, just tried it dont work :(

i am trying to use windows' boot.ini as my boot loader rather than grub or lilo, Lilo wouldn't install in either 5.04 or 5.10 so i had to install grub, which wouldn't install on my partition only as MBR. what do i need to do to get boot.ini to be able to boot correctly into both linux and windows.

P.S linux is on my slave    dev/hdd1

---

### Post by kairu0 on 2005-12-10
Okay, if you can't install GRUB on the partition, then here is what I would do. First, ditch using the Windows bootloader. Go into your computer's BIOS and set it to boot off of your second hard drive first. Now, when you boot up you will get Grub and it will hopefully already have a Windows option in it. If it doesn't, it's not a big deal to put it in. Here's how mine is configured in /boot/grub/menu.lst:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda4
title		Windows NT/2000/XP (loader)
root		(hd0,3)
savedefault
makeactive
chainloader	+1


```

(hd0,3) = first drive, 3rd partition. In your case, this will probably be (hd0,0).

---

### Post by radiotalent on 2005-12-10
I recently used [BootPart]("http://www.winimage.com/bootpart.htm") to adjust the boot.ini file in the Windows partition.  It was very quick to do (from Windows) and works fairly well when Windows is on the primary master disk.

For someone a bit queasy about really mucking around with the Windows settings its definitely something to look at.

---

### Post by maccom on 2005-12-10
unfortunately i HAVE to use windows bootloader as i am not the only person who uses this pc, and windows bootloader they can cope with, grub they can't!

so is there something i can do??

---

### Post by linbetwin on 2005-12-10
[quote=maccom]unfortunately i HAVE to use windows bootloader as i am not the only person who uses this pc, and windows bootloader they can cope with, grub they can't!

so is there something i can do??[/quote]

You can configure GRUB to boot into Windows by default and shorten the time delay to, say, 3 seconds.

Or you can put GRUB on a floppy, configure the BIOS to boot from floppy first, and use that floppy only when you want to boot into Ubuntu.

Or you can use the LiveCD to boot into Ubuntu.

---

### Post by maccom on 2005-12-10
YEY! 
I got GRUB to install on on my partition!
ok...so wot next??

---

### Post by aysiu on 2005-12-10
There are two ways to dual boot:

1. Install Grub to the MBR.
Grub will automatically recognize Windows and add it to the boot menu.
When you boot up, you'll get a choice between Windows and Ubuntu.
You do **not** have to modify the boot.ini file in any way.

2. Install Grub to somewhere else (a floppy or whatever), then somehow convert it to a file that Windows can use (I've seen *linux.bin* used in some instructions). You copy that file to Windows and then edit the boot.ini file to recognize Ubuntu and linux.bin file. Then Windows' boot loader will let you choose between Ubuntu and Windows.

Uh... method #1 is a lot easier!

There's a tutorial for method #1 here:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

and a tutorial for method #2 here:
[http://ubuntuforums.org/showthread.php?t=80508](http://ubuntuforums.org/showthread.php?t=80508)

---

### Post by maccom on 2005-12-10
I put grub on a floppy disk, when i boot with it in, i get "GRUB _"  and nothing else, in windows explorer there arent any files on the floppy disk!?!?!

---

### Post by aysiu on 2005-12-10
I don't vouch for method #2. I'm just telling you it exists and that there are tutorials for it. I tried it once, and it was a big turnoff to me from Linux because I thought that was the way you were supposed to configure a dual boot.

Method #1 has *always* worked for me. Install Grub to the MBR. That takes care of everything.

---

### Post by kairu0 on 2005-12-10
If you used GRUB and made Windows the default would they know the difference?

You could also use a boot disk for when you want to use Linux. That's another option.

---

### Post by maccom on 2005-12-11
ok thanks for all your help,
I amanged to get grub to install on my pertition and then used partboot to make the boot.ini work.

Thanks for all your help
[maccom.1.vg](maccom.1.vg)

---

### Post by trjtrj on 2005-12-17
[QUOTE=maccom]unfortunately i HAVE to use windows bootloader as i am not the only person who uses this pc, and windows bootloader they can cope with, grub they can't!

so is there something i can do??[/QUOTE]

my answer would be to use grub and teach the other users how to select the windows option at the bottom of grub's list.

---

