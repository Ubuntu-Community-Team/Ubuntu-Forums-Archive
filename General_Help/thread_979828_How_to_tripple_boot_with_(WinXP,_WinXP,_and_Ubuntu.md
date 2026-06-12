---
title: "How to tripple boot with (WinXP, WinXP, and Ubuntu 8.10)?"
date: 2008-11-12
forum: General Help
---

### Post by Cheese Grits on 2008-11-12
The main hard drive on my desktop pc has three partitions.  The first two partitions are loaded with different installs of XP.  The first is my general home computer.  The second is a stripped down version of XP that I use for audio production.  

After installing XP, I installed Ubuntu 8.10 on the third partition.  I expected the GRUB bootloader to run at startup and recognize each OS.  Instead, it seems that GRUB is not working at all, and the Windows bootloader is still booting at startup.  Of course, it doesn't recognize Ubuntu.

Is there a good step-by-step guide that will help me figure out how to get GRUB to run at startup so that I can boot linux without having to install a live CD?

I'm a linux noob, fyi.

Thanks in advance.

---

### Post by crazyness003 on 2008-11-12
This [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5) shows you how to restore GRUB to the MBR but im not sure how to get the chainloader to boot separate XP partitions.

Try
```
title        Windows XP Main
root        (hd0,0)
#savedefault
# this is to set this particular entety as the default, just remove the #
makeactive
chainloader    +1

title        Windows XP Audio Production
root        (hd0,1)
#savedefault
# this is to set this particular entety as the default, just remove the #
makeactive
chainloader    +1
```Of course im only assuming thats how your hdd is partitioned. You need to know exacly what partitions each install occupies. In GRUB speak you'll have (hd[harddrive, starting with '0'],[partiton starting with '0'] . Like (hd0,0) is the first HD, first partition.
In Linux-speak its sd[harddrive, starting with "a"][partition, startign with '1']. like sda1 is the first hardrive, first partition.
In windows...i have no idea

---

### Post by TeXtonyx on 2008-11-12
This is how I boot XP and Ubuntu, from my boot.ini (not MBR, but /boot grub)

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="MS XP Professional"
/noexecute=optin /fastdetect
C:\UbuntuB.bin="Ubuntu"
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

--------------------------------

Suppose I had another XP OS installed on the second partition,
then I could add to boot.ini the next entry, changing the 1 to 2

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Win XP Pro II"
/noexecute=optin /fastdetect

---

### Post by Cheese Grits on 2008-11-12
> **TeXtonyx said:**
> This is how I boot XP and Ubuntu, from my boot.ini (not MBR, but /boot grub)

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="MS XP Professional"
/noexecute=optin /fastdetect
C:\UbuntuB.bin="Ubuntu"
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

--------------------------------

Suppose I had another XP OS installed on the second partition,
then I could add to boot.ini the next entry, changing the 1 to 2

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Win XP Pro II"
/noexecute=optin /fastdetect

So, with this method, I would simply edit my boot.ini file?  Obviously I would make a copy first.  Would this be working through the windows boot loader or GRUB?

---

### Post by crazyness003 on 2008-11-12
> **Cheese Grits said:**
> So, with this method, I would simply edit my boot.ini file?  Obviously I would make a copy first.  Would this be working through the windows boot loader or GRUB?

I dunno. if that works, awesome! but i dont think the win bootloader can handle working with anythign but win.

godspeed

---

### Post by ManyBeers on 2008-11-12
> **Cheese Grits said:**
> So, with this method, I would simply edit my boot.ini file?  Obviously I would make a copy first.  Would this be working through the windows boot loader or GRUB?
In order to use this method which i also use to boot Ubuntu you must make a copy of Grub's Stage one and place it in the root of C:\(assuming C:\ is where your first Windows partition is)or whatever is your boot partition.

---

### Post by Slim Odds on 2008-11-12
> **crazyness003 said:**
> I dunno. if that works, awesome! but i dont think the win bootloader can handle working with anythign but win.


Actually, booting from the Win bootloader is quite easy.

When you install Ubuntu (for example), don't install grub on the MBR. Instead, put it in the 1st sector of the ubuntu partition.

Then make a copy of that sector (it's only 512 bytes). Put it in the c:\ directory. Call it something like ubuntu.bin or something.

Then make a new entry in the Win bootloader and tell it to load that file.

That's all it takes.

---

### Post by crazyness003 on 2008-11-12
> **Slim Odds said:**
> Actually, booting from the Win bootloader is quite easy.

When you install Ubuntu (for example), don't install grub on the MBR. Instead, put it in the 1st sector of the ubuntu partition.

Then make a copy of that sector (it's only 512 bytes). Put it in the c:\ directory. Call it something like ubuntu.bin or something.

Then make a new entry in the Win bootloader and tell it to load that file.

That's all it takes.

Thats interesting. didnt know it. But i still like grub better. Im sure it comes in handy from time to time

---

### Post by TeXtonyx on 2008-11-13
OP:"So, with this method, I would simply edit my boot.ini file? 
Obviously I would make a copy first. Would this be working through 
the windows boot loader or GRUB?"
---------------------
> **crazyness003 said:**
> I dunno. if that works, awesome! but i dont think the win bootloader can handle working with anything but win. godspeed
------------------------

To the OP first: I wrote, "This is how I boot XP and Ubuntu, from 
my boot.ini (not MBR, but /boot grub)."

The default Ubuntu install puts grub in the MBR, the method that 
I suggest puts grub into the Ubuntu /boot partition. I think it
is an advantage for people who dual boot Windows and Ubuntu, 60%,
to have grub installed to the /boot because it's more flexible.

I'll make some comments about the boot.ini. Adding your other XP
OS is a simple cut and paste of your default OS entry and an edit
of a 1 to a 2. If you had a second hard drive, one would cut and
paste and change the drive number from 0 to 1. I usually change
the title that appears on the menu screen even though I can tell
from its position. 

There are advantages to having grub in the /boot partition. Night
before last I tried to upgrade 8.04 to 8.10 over the internet and
it failed. I could no longer boot into 8.04 even, I had to reinstall.
If grub is installed in the MBR, then, when Ubuntu gets corrupted
for any reason, the grub support files on the Ubuntu partition 
are no longer available and you can't boot XP, since those boots
are controlled by the MBR grub. Or if you decide to uninstall
Ubuntu, you can't boot XP. Yes, you can use Recovery Console to
fixmbr and fixboot. Maybe you forgot where the cd is. When grub
is in the MBR it makes XP depend upon Ubuntu. The second XP OS
depends upon Ubuntu when grub is in the MBR.

I prefer a standalone approach. By putting grub in the /boot one
can still boot XP even if Ubuntu fails. If XP fails, no ntldr,
then you can still boot Ubuntu with a Super Grub disk. Now as a
type of backup, I put the XP entries into the grub menu.lst that
is on the Ubuntu partition. So that if XP OS#1 fails I can boot
XP OS#2. This strategy is useful in more advanced situations.

On my other computer, I have XP and Ubuntu on sda. I have Vista
and Ubuntu (used to be OpenSuse) on sdb. I can boot XP and either
Ubuntu from boot.ini. From Ubuntu I can boot Vista or XP. From 
Vista, if I choose from bios to boot hd1, I can boot Vista or
Ubuntu which can boot XP. This type of redundancy makes your system
less fragile. Suppose the XP partition on sda goes out. I could
still boot Ubuntu from the Super Grub disk. From Vista, I could
still boot either Ubuntu without the Super Grub Disk. That uses
Easybcd. In your case, just using XP and Ubuntu, download Bootpart. [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm) bootpa26.zip  It's
very easy to use. It writes 512 bytes of the boot sector to your 
C:\ root drive and makes an entry into boot.ini I am going to post
a few links later. The dd method of copying 512 bytes and using Bootpart
are not equivalent. I have Ubuntu on the second drive of this
machine. dd doesn't work for ubuntu.bin for that drive, only if
Ubuntu is installed on the same drive. But Bootpart works for
the second drive. That is why you saw a UbuntuB.bin, it's for
my second drive. I used to have a UbuntuA.bin for my first drive.

----------------------------
crazy*: Well, you have evidence now that this method works for
Windows and Linux. It does use grub, but in a more flexible way,
not putting all the eggs in one basket=MBR.

I'll provide some links from the internet for proof of the pudding
is in the eating.

[http://www.hollenback.net/index.php/WindowsLinuxDualBoot](http://www.hollenback.net/index.php/WindowsLinuxDualBoot)
Philip said he hadn't tested the equivalence of dd and Bootpart
in the context of two drives. They function the same way when
Windows and Ubuntu are on the same drive by using the dd method,
but dd doesn't seem to work when spanning drives. dd works when
created on the second drive when Ubuntu is on the second drive,
but not using the dd 512 made from the second drive on first drive. 

[http://ubuntuforums.org/archive/index.php/t-499904.html](http://ubuntuforums.org/archive/index.php/t-499904.html)

[http://forums.majorgeeks.com/showthread.php?t=108021](http://forums.majorgeeks.com/showthread.php?t=108021)
c:\> bootpart

When you run it, you get a report similar to the one below:

Physical number of disk 0: ffff6a32
0 : C:* type=42 , size=22659651 KB, Lba Pos=63
1 : C: type=42 , size=17358232 KB, Lba Pos=45319365
Physical number of Disk 1 : ca1dca1d
2 : D: type=83 <Linux native>, size=6184993 KB, Lba Pos=63
3 : D: type=82 <Linux swap>, size=522112 KB, LBA Pos=12370050
4 : D: type=83 <Linux Native>, Size=1542240 KB, LBA Pos=13414275

So the command to make a ubuntu.bin for sdb(1) would be
C:\> bootpart 2 ubuntuB.bin "UbuntuB"
puts ubuntuB.bin in C: root and makes an entry to boot.ini UbuntuB
If there was a type 83 reported on C: you could substitute that #

---

### Post by Cheese Grits on 2008-11-18
I'm no longer having trouble booting Windows with Grub, but I cannot seem to boot Ubuntu with grub.  :mad:

Thanks to all for the advice and guidance, but I think I'm missing something very basic.

I edited the menu.lst file, and in doing so I changed the title of "Ubuntu 8.10 XXXXXXXXXXXXXXXXXXXXX" (where XXXXXXXX=a bunch of stuff I don't recall of the top of my head) to "Ubuntu 8.10".  After that, I cannot boot Ubuntu.  Because I can't get into Ubuntu, I can't change the menu.lst file back.

Can someone help with this?

Thanks in advance.

---

### Post by crazyness003 on 2008-11-18
> **Cheese Grits said:**
> ... I cannot seem to boot Ubuntu with grub.  :mad:....
I edited the menu.lst file, and in doing so I changed the title of "Ubuntu 8.10 XXXXXXXXXXXXXXXXXXXXX" (where XXXXXXXX=a bunch of stuff I don't recall of the top of my head) to "Ubuntu 8.10".  After that, I cannot boot Ubuntu.  Because I can't get into Ubuntu, I can't change the menu.lst file back.

You can edit grub if you boot up from a liveCD. And after doing that, you can probably use my grub menu
```
title        Ubuntu 8.10, kernel 2.6.27-8-generic
uuid        5d0616d8-4c03-4291-aaf8-4a8619f7eccc
kernel        /boot/vmlinuz-2.6.27-8-generic root=UUID=5d0616d8-4c03-4291-aaf8-4a8619f7eccc ro quiet splash 
initrd        /boot/initrd.img-2.6.27-8-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-8-generic (recovery mode)
uuid        5d0616d8-4c03-4291-aaf8-4a8619f7eccc
kernel        /boot/vmlinuz-2.6.27-8-generic root=UUID=5d0616d8-4c03-4291-aaf8-4a8619f7eccc ro  single
initrd        /boot/initrd.img-2.6.27-8-generic

title        Ubuntu 8.10, memtest86+
uuid        5d0616d8-4c03-4291-aaf8-4a8619f7eccc
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP Ultimate
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

the only proble i see with this is that i dont know if your 
> uuid        5d0616d8-4c03-4291-aaf8-4a8619f7eccc
kernel        /boot/vmlinuz-2.6.27-8-generic root=UUID=5d0616d8-4c03-4291-aaf8-4a8619f7eccc ro quiet splash 
initrd        /boot/initrd.img-2.6.27-8-genericis the same?

So, id look around if a grub reinstall my be a viable options (but then risk killing your working windows boot)

Sorry, i dont know too much about this either.

Anybody else?

---

### Post by TeXtonyx on 2008-11-18
I think you can use most of the 8.10 that crazyness003 provided but
$ sudo blkid /dev/sda1  

I think you said your OS's were all on one drive.

From the terminal:
$ blkid /dev/sda1  produces your actual UUID. Substitute it in the 
portion of menu.lst for 8.10 that crazyness033 provided. copy&paste


Also fstab keeps track of partions by UUID so check for consistency.

Also when you use the live cd to boot Ubuntu, you can use 
gksudo nautilus 
and then navigate to /boot/grub/menu.lst click (or double-click on it)
and you can do your editing of fstab , it is in /etc/fstab

---

### Post by Cheese Grits on 2008-11-19
I guess I'm having trouble booting from the live CD.  When I place the CD into the drive and turn the computer on, I get a menu which looks like this:

[IMG]http://images.howtoforge.com/images/perfect_setup_ubuntu610/1.png[/IMG]

The options include:  (a) install to the hard disc; (b) check CD for defects; (c) rescue a broken system; (d) memory test; and (e) boot from first hard disc.

I don't see any option to boot to a live version.  Before I installed Ubuntu, there was an option to "try ubuntu without any change to your computer".

So, am I just a complete moron?  How do I boot ubuntu from the live CD?

---

### Post by TeXtonyx on 2008-11-19
I haven't encountered this problem. I would try "rescue a broken
system". It seems at the least it would give you a command line
and you could try :  gksudo gedit /boot/grub/menu.lst
and maybe gedit will open so you can make changes to the 8.10 
part of your menu.lst file.

Maybe the only difference will be that it won't have the install
icon on the desktop since you've already installed Ubuntu.

I think you can get two terminals going, one to run gedit
and one to run $ sudo blkid /dev/sda1 
so that you can compare the UUID numbers.
I remember something about tune2fs vaguely, but that's for later.

Also check to see if you system made a backup of menu.lst,
something like menu.lst.bak~ Maybe there is a backup file
of your older working menu.lst file (also in the grub directory).

If you find such a backup file, then you can 
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.TMP 

which makes a backup of your current not working menu.lst file.
Only if you've found a previous backup of menu.lst you can
sudo rm menu.lst  (which is your current not working menu.lst)

Then sudo cp /boot/grub/menu.lst.bak /boot/grub/menu.lst
(you've changed the name of your backup menu.lst.? to menu.lst)

I don't know what the real name of the menu.lst backup file
will be or if you will really have one, it is something to check 
for to make this easier. If you find a file that might be
the backup, look it over first with gedit. 

I haven't dealt with the problem you just now reported. So I'm
trying to come up with some ideas. Hunting for a backed up
copy of your menu.lst is the best I could think of. Choosing
rescue a broken system should give you some control.

---

### Post by Slim Odds on 2008-11-19
> **Cheese Grits said:**
> 
The options include:  (a) install to the hard disc; (b) check CD for defects; (c) rescue a broken system; (d) memory test; and (e) boot from first hard disc.

I don't see any option to boot to a live version.  Before I installed Ubuntu, there was an option to "try ubuntu without any change to your computer".

So, am I just a complete moron?  How do I boot ubuntu from the live CD?

It sounds like you have the alternate CD, not the Live CD.

---

### Post by Cheese Grits on 2008-11-19
> **Slim Odds said:**
> It sounds like you have the alternate CD, not the Live CD.

I don't think I knew there was a difference.  I'll look into this.  Thanks. :)

Edit:  I think I did have the alternate CD.  I'll check the difference when I get home tonight.  I can't believe it only took about 3 minutes to download the entire iso torrent. :shock:

---

### Post by Cheese Grits on 2008-11-20
So, I definitely had the alternate CD previously.  Use of the live 64-bit CD enabled me to run linux live.  Thanks to everyone for all the help so far.  I think my only remaining issue might be with menu.lst.  Tonight, when I get a chance, I'll copy and paste the contents here.

Thanks again!

---

