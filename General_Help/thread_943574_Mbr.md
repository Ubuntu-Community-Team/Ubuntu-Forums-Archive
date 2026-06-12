---
title: "Mbr"
date: 2008-10-10
forum: General Help
---

### Post by gmlinux on 2008-10-10
Need a little help here.
I have 2 hard drives in my PC, one with XP and one with Ubuntu.
I want to format the drive that contains XP but my MBR resides there.
If I format that drive will I still be able to boot Ubuntu?

---

### Post by SuperSonic4 on 2008-10-10
Yes. You just need to tell your bios to go to your ubuntu drive first

---

### Post by caljohnsmith on 2008-10-10
> **gmlinux said:**
> Need a little help here.
I have 2 hard drives in my PC, one with XP and one with Ubuntu.
I want to format the drive that contains XP but my MBR resides there.
If I format that drive will I still be able to boot Ubuntu?
If you can tell your BIOS to boot the Ubuntu drive, and if the Ubuntu drive has Grub installed in its MBR, you should be able to boot it fine (but choosing an OS from the Grub menu may not necessarily work). When you say your MBR resides on your XP drive, do you mean Grub is installed in the MBR of your XP drive?

---

### Post by gmlinux on 2008-10-10
I tried that suggestion and it was a no-go.
As for the second reply, I'm not a Linux pro, when the computer boots I get a choice of Ubuntu or XP. I may not be explaining this too well.

---

### Post by caljohnsmith on 2008-10-10
OK, boot into Ubuntu, or if you can't do that any more, boot your Ubuntu Live CD, open a terminal (applications > accessories > terminal), and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Go ahead and reboot, make sure you have your BIOS set to boot your Ubuntu drive, and when you get the Grub menu, select Ubuntu, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent if it works.

If it works, once you get into Ubuntu, open a terminal again and do:
```
gksudo gedit /boot/grub/menu.lst
```
And change all your Ubuntu entries in that file to use the (hd0,Y) that worked instead of the "root (hdX,Y)" that they will have. Also change the "#groot=(hdX,Y)" line to use the same (hd0,Y) that worked. Save and you should be done. Let me know how it goes or if you run into problems.

---

### Post by gmlinux on 2008-10-10
Well that almost did it.
Guess I didn't edit the menu.lst correctly, as I get an error and won't boot. Error 15 I think it was.
Do I have to replace EVERY hd1.0 with hd0,y?

---

### Post by gmlinux on 2008-10-10
As I said before, I'm no Linux pro, so bear that in mind.
Some thoughts I have, the drive with XP installed is the master and the drive with Ubuntu is Slave. This is in the BIOS. when I did as you asked in terminal........grub> find /boot/grub/stage1.............
it returned.......hd1,0...........   Would this not be the drive where Ubuntu is installed?   If I do the change........hd0,y..........  when I edit the entry in the boot selection, what does that mean?  I would expect it to refer to the drive with XP installed on it. As you can see, I am completely confused.

---

### Post by caljohnsmith on 2008-10-10
Did you change your BIOS to boot your Ubuntu slave drive first? If you can do that, then the directions from post #5 should work. If you are still booting Grub from your XP drive, then those directions won't work because Ubuntu will then be on a drive different from the boot drive, and your Grub menu would have to be modified differently. I'm just trying to point out that if you can boot your Ubuntu drive on start up, then you can do whatever you want with your XP drive, including formatting its MBR and everything else, so booting the Ubuntu drive is key here--can you set your BIOS to do that?

---

### Post by gmlinux on 2008-10-10
Yes Ichanged the Bios and rebooted and I get the screen where I have the three choices but won't go any further. This is where I get the error.
My memory won't let me tell you what the error was, but something about the menu.lst

---

### Post by gmlinux on 2008-10-13
OK, we are into Thanksgiving week-end here and a 50th anniversary so I am not too active with the PC, will give it another go in a day or two.
Thanks for the info.

---

### Post by gmlinux on 2008-10-14
Hectic week-end over with, trying again.
I'm pouring out my stupidity here, not much headway made.
I boot with my CD.
I opened a terminal and done    sudo grub
Then I done                     grub> find/boot/grub/stage1 
The reply is                    hd1,0
I then do                       grub> root (hd1,0)
Next                            grub> setup (hd1)
Next                            grub> quit
After this has been done, I restart the computer without the CD
and set my bios to boot on  hd1
Now when I boot I get the grub menu and I make a selection from this menu, normally the first one on the list,and I get an error which says.........error15: file not found.........
What have I done wrong, not done, or what am I missing?

---

### Post by caljohnsmith on 2008-10-14
OK, getting that Grub error when selecting to boot Ubuntu just means that you need to edit your Grub's menu.lst. Follow the directions at the end of post #5 where it starts "Go ahead and reboot..." and that should work.

---

### Post by gmlinux on 2008-10-14
OK  Tried that and I get an error
error 11: unrecognized device string

---

### Post by caljohnsmith on 2008-10-14
OK, from your Live CD, post the output of:
```
sudo fdisk -lu
sudo mount /dev/sdb1 /mnt
cat /mnt/boot/grub/menu.lst
```

---

### Post by gmlinux on 2008-10-14
As a precaution, for me, is there a typo in the first line?

sudu

---

### Post by caljohnsmith on 2008-10-14
Yes, sorry about that, I corrected it above.

---

### Post by gmlinux on 2008-10-14
Here is what I get.





ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb05db05d

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   160826714    80413326    c  W95 FAT32 (LBA)

Disk /dev/hdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000061f8

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63   150191684    75095811   83  Linux
/dev/hdb2       150191685   156248189     3028252+   5  Extended
/dev/hdb5       150191748   156248189     3028221   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
mount: special device /dev/sdb1 does not exist
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
cat: /mnt/boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-10-14
So what version of Ubuntu are you using? Also, please post the output of:
```
sudo mount /dev/hdb1 /mnt
cat /mnt/boot/grub/menu.lst
```

---

### Post by gmlinux on 2008-10-14
As you can see there was no response to the first command
Version is 8.04





ubuntu@ubuntu:~$ sudo mount /dev/hdb1 /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd1,0)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f84dfa79-7a9f-4816-a572-31927ddf82a2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 8.04, kernel 2.6.24-17-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=f84dfa79-7a9f-4816-a572-31927ddf82a2 ro quiet splash
initrd          /boot/initrd.img-2.6.24-17-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=f84dfa79-7a9f-4816-a572-31927ddf82a2 ro single
initrd          /boot/initrd.img-2.6.24-17-generic


title           Ubuntu 8.04, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-10-14
OK, while hdb1 is still mounted on /mnt, do:
```
gksudo gedit /mnt/boot/grub/menu.lst
```
Change all the "root (hd1,0)" lines in the Ubuntu entries to use:
```
root (hd0,0)
```
And also change the groot line so it is:
```
#groot=(hd0,0)
```
And lastly, at the end of that file, replace the Windows entry with:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

```
Save, reboot, and let me know what happens. :)

---

### Post by gmlinux on 2008-10-14
Wish I had a webcam so you could my smile.
Grub menu came up and when I selected the top item on the list it booted.
I didn't try the XP selection to see if that worked. I only keep XP for one program, so it wouldn't be the end of the world.
Is there anything else to do to finish this off?

---

### Post by caljohnsmith on 2008-10-14
Glad it's finally working, gmlinux. I can't think of anything else you would need to do. Anyway, have fun with it. :)

---

### Post by gmlinux on 2008-10-14
Thank you very much, your assistance and knowledge is greatly appreciated. I was afraid I was going to lose a lot of saved info and pictures etc, but thanks to you it isn't happening.
All the best, have a great day.

---

