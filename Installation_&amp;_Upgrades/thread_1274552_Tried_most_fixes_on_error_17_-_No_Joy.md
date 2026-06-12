---
title: "Tried most fixes on error 17 - No Joy"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by Oldest Bob on 2009-09-24
Had Windows on base 80 gig drive. Added new 10 gig drive and installed Ubuntu and all worked well in dual boot. Windows had problem so just used Linux until tried to udate to Ubuntu 9.04 and told "not enough memory" Decided to forget Windows so installed 8.1 on the 80 gig drive and get Grub error 17 no matter what I do. Not being very computer literate, I'm stuck  and need **_HELP - HELP -HELP_**
1. Have read most threads throughout "Installation & Upgrades" and tried their solutions
--Tried "root (hd0,0) then setup (hd0) but get "error 17 -cannot mount partition".
-- Checked drive ID and its OK
-- Saw approach that said his system worked when he put both Windows and Linux on same drive (reducing size of Linux partitions). I reinstalled on 80 gig drive and tried to manually partition; using only 12 gig for basic plus small swap partition. I did something wrong (as usual) and was told there were errors so that didn't work. 
-- Have reinstalled at least four times.
  Does anyone have any other ideas for me as I am about to give up.
I hope someone can help me as I have spent weeks trying to get my system operating other than on live CD.

---

### Post by rreese6 on 2009-09-24
Error 17 usually means that the hard drive is not being identified corectly. the problem in in the file called mneu.lst

boot up live-cd
open terminal and type this:

fdisk -l
that will tell you what your partitions are
post here what you get....once we know the where linux is installed,
we will got there and edit the menu.lst file so your system boots.
Most likely the boot pointer is looking at windows and not Linux.
but we will see.

---

### Post by Oldest Bob on 2009-09-25
> **rreese6 said:**
> Error 17 usually means that the hard drive is not being identified corectly. the problem in in the file called mneu.lst

boot up live-cd
open terminal and type this:

fdisk -l
that will tell you what your partitions are
post here what you get....once we know the where linux is installed,
we will got there and edit the menu.lst file so your system boots.
Most likely the boot pointer is looking at windows and not Linux.
but we will see.







here is result from fdisk
bash: fddisk: command not found
bob@bob-desktop:~$ fdisk -l
bob@bob-desktop:~$ sudo fdisk -l
[sudo] password for bob:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xb74510e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8814    66633808+   7  HPFS/NTFS
/dev/sda2            8815       10337    11513880    f  W95 Ext'd (LBA)

Disk /dev/sdb: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x062cf0b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1158     9301603+  83  Linux
/dev/sdb2            1159        1216      465885    5  Extended
/dev/sdb5            1159        1216      465853+  82  Linux swap / Solaris

By the way - I reinstalled 7.1 on my 10 gig drive with no problem. I think that either my 8.1 disk is bad or an 80 gig drive is too big to use.

---

### Post by Oldest Bob on 2009-09-25
here is result from fdisk
bash: fddisk: command not found
bob@bob-desktop:~$ fdisk -l
bob@bob-desktop:~$ sudo fdisk -l
[sudo] password for bob:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xb74510e2

Device Boot Start End Blocks Id System
/dev/sda1 * 1 8814 66633808+ 7 HPFS/NTFS
/dev/sda2 8815 10337 11513880 f W95 Ext'd (LBA)

Disk /dev/sdb: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x062cf0b7

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 1158 9301603+ 83 Linux
/dev/sdb2 1159 1216 465885 5 Extended
/dev/sdb5 1159 1216 465853+ 82 Linux swap / Solaris

By the way - I reinstalled 7.1 on my 10 gig drive with no problem. I think that either my 8.1 disk is bad or an 80 gig drive is too big to use.

---

### Post by rreese6 on 2009-09-25
ok good, now that we have that post your menu.lst contents here.
menu.lst is found in the folder /boot/grub.

You may need the mount the drive to get access
if you do then goto /media
sudo mkdir sdb1
sudo mount /dev/sdb1 /media/sdb1
then cd /media/sdb1/boot/grub
ls -l
you should see menu.lst there, copy and post here.

---

### Post by Oldest Bob on 2009-09-26
here ism menu.lst
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=2356673e-b184-4e0f-b3ee-47353a922945 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2356673e-b184-4e0f-b3ee-47353a922945 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2356673e-b184-4e0f-b3ee-47353a922945 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=29232bb0-ee92-4c3a-92c3-981839381c8e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=29232bb0-ee92-4c3a-92c3-981839381c8e ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by rreese6 on 2009-09-26
This is a bit confusing. 
Your menu.lst shows two installations of Linux
7.10 on the second drive (80 gig)(sdb1)
and 8.10 on the first drive (10 gig).(sda1)
However fdisk -l reports that you have Windows on the first drive.(sda1).

My question is this are you making changes between posting information here?
if not then I have the fix, but I need to be sure about the current fdisk -l

re-run that command and check it against the post. if it is the same let me know, otherwise post the new data.

Also are these new installs? It might be easier just to wipe the slate clean and start fresh...either way is fine with me.
BTW if you have aol aim(windows) or pidgin (linux) my user name is reeserh2 we can take this live. I am online now

---

### Post by Oldest Bob on 2009-09-26
No I am not doing any installation between replies.
Yes I installed 8.1 on disk 1 (80 gig) and because I never could get past the grub error 17 I reinstalled 7.1 on my second disk(10 gig) I also noted that windows seemed to still be on disk 1, but didn't know what to do about it.  The last time I tried to reinstall 8.1 on disk 1 I clicked on FORMAT.in the partitioning but that didn't seem to make any difference. Here is current output of fdisk:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xb74510e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8814    66633808+   7  HPFS/NTFS
/dev/sda2            8815       10337    11513880    f  W95 Ext'd (LBA)

Disk /dev/sdb: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x062cf0b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1158     9301603+  83  Linux
/dev/sdb2            1159        1216      465885    5  Extended
/dev/sdb5            1159        1216      465853+  82  Linux swap / Solaris
bob@bob-desktop:~$

---

### Post by Oldest Bob on 2009-09-26
> Disk /dev/sdb: 10.0 GB, 10005037056 bytes
> 255 heads, 63 sectors/track, 1216 cylinders
> Units = cylinders of 16065 * 512 = 8225280 bytes
> Disk identifier: 0x062cf0b7
> 
>    Device Boot      Start         End      Blocks   Id  System
> /dev/sdb1   *           1        1158     9301603+  83  Linux
> /dev/sdb2            1159        1216      465885    5  Extended
> /dev/sdb5            1159        1216      465853+  82  Linux swap / Solaris
> bob@bob-desktop:~$ 
>

---

### Post by Oldest Bob on 2009-09-26
rreese6. I seem to have goofed an your last message re getting updated menu.lst. please send it again as I am not on aol or pidgen.

---

### Post by rreese6 on 2009-09-26
ok good. 
this is where are problem is. one of the drives still has a Windows partition and the the grub thinks it should be Linux...result error 17.

Just to be sure I don't get this wrong(I am Old too) post the contents of /etc/fstab here next, then I will get to work.

brb making a cup of tea.

---

### Post by rreese6 on 2009-09-26
Although I would still like for you to post the 

"fstab" file from /etc .... I will continue

download the attached file. then

```
cd /media/sdb1/boot/grub
sudo cp menu.lst menu.lst.bad

```
take the attached file and rename it from menu.txt to menu.lst
and put it in the /boot/grub/ folder

Basically we are backing up your file and replacing your old menu.lst file with one I modified.

do a ls -l to make sure it is there.
then reboot the machine.
if I figure right, grub should start unless fstab file is wrong...need to post that here if we fail.
you will have two choices, ubuntu or windows. I think the windows will error but ubuntu should boot.(text style no splash)

---

### Post by Oldest Bob on 2009-09-26
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=2356673e-b184-4e0f-b3ee-47353a922945 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=370e992c-62a2-4207-9b66-d849fe0f69bc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by rreese6 on 2009-09-26
if that file I gave you did not work.

do the same as in post #12 but use this one:
 change name from menu_2.txt to menu.lst.

oh one other thing.
once you copy it over to /media/sdb1/boot/grub
ls -l and make sure the owner is root
if not then
```
sudo chown root:root menu.lst
```

---

### Post by Oldest Bob on 2009-09-26
Not sure what you are doing in menu.txt. It seems to be related to Ubuntu 7.1 which i have on drive sdb2 and is working perfectly. Shouldn't menu.txt refer to 8.1 which is what I want installed sda1??

---

### Post by Oldest Bob on 2009-09-26
reese6. I have to pull off line. I wont be able to get back until Sunday evening. Sorry. I really appreciate your help as I see what you are doing and sure wish I could finish but I just can't. Thanks much .Bob

---

### Post by rreese6 on 2009-09-26
Well normally yes, but the problem is that 8.10 is not actually on sba1 according to fdisk -l.
it says windows is there.
and the menu.lst even though it said to boot 8.10 off of sda1, it could not because you have the the wrong file system there (NTFS) ..Windows
that is what cased the error 17.

now that we at least have grub working again. we can go clean up sda
and install 8.10 on it.

from 7.10 ubuntu, open a terminal and type 
```
gparted
```

that will open the partitioner, gparted.
it will scan your drives.
up in the right corner is the device selection, choose /dev/sda
once that reads you should see  windows partitions there.
delete those (by clicking on one at a time and select delete)
once that is done, click apply.
the 80 gig drive will now be empty. 
you can now make a couple partitions (root and swap) if you like. or just close it and run your 8.10 install disk and put ubuntu 8.10 on the whole drive (/dev/sda).

---

### Post by rreese6 on 2009-09-26
ok Bob, see you Sunday, I am subscribed to this post so I will notice when you get back. you are almost finished too.. :)

---

### Post by Oldest Bob on 2009-09-27
Here is /etc/fstab " [B]aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0[/B] "

I went to gparted and deleted sda1 and sda2. I tried to reinstall 8.1 from my disk . I selected the standard first option to let the installed handle the whole problem but I get message that errors were found and should go back to the partition menu and fix them. I don't see a list of errors nor any way to fix them in the partition menu. I then trid the option to contue with error present and got the message that partion could not be mounted.  I haven't tried to fix  menu.lst yet but will start now by downloading your version as you directed.

---

### Post by Oldest Bob on 2009-09-27
rreese6 I on again and still need help

---

### Post by Oldest Bob on 2009-09-27
rreese6
 As noted above I went to gparted and deleted partitions in sda drive . I reinstalled 8.1 on drive 1 (sda1) I downloaded menu_2.txt and made it the menu.lst file. I shut down and rebooted. The boot menu started with Linux 7.1. It showed "Other Operating systems" and noted ****"windows - maybe, but definitely not Linux".**** 
I must close down again but if you have any other ideas I'll check tomorrow.

---

### Post by rreese6 on 2009-09-28
bob, 
Sorry I did not get back to you sooner, I was very involved in and ethernet problem that we finally had to hack to make work...after 2 days of working on it.

menu2.lst was not to be used after the test.
if you are going to reinstall the OS, then may I suggest
you do it like I would?
Remove the HD you don't want to use as your main system (most likely the 10 gig HD)
Make sure the 80 gig is the primary master (look at bios)
then insert LiveCD and exit BOIS Settings.
Once the desktop is up.
chose install icon
when it is time to partition, tell it to use the entire disk.
finish installation and reboot.
your system should be up...do your updates....
now to have the other drive,
power down and install the next drive (it will be now known as sdb)
power up and run garted to delete all the partitions on the 10 gig drive.
now the drive is ready to use for whatever you wish.
Just remember it is now (HD1,0) in Grub-speak or sdb in Linux-speak
so if you want to install another Linux on it do so and write the grub to the same drive. then you go to the /boot/grub/ of that drive (sdb) and look at the menu.lst file to see the titles of the new Linux install. you can copy those "Title"s and paste them into the menu.lst of the first drive (sda)...under the same directory structure (/boot/grub)... that way you will have both drives in the grub menu in the order of Original install(first drive 80gig) then extra install(second drive 10gig).

I can help you through this if you like. Send me a PM...or instant message on MSN rreese6

---

### Post by Oldest Bob on 2009-09-29
rreese6. Early in my problem I unplugged my 10 gig drive and tried a new installation on my 80 gig drive from my 8.1 disk . I selected "Use entire disk" in the partitioning. I got the same old grub error 17. I did not,however, check my BIOS to see that it was the primary disk. Is that likely to be a prolem when only s single disk is installed?
I repartiioned  my 80 gig drive. gparted now shows:
    /dev/sda1   ext3               26.3 gb
    /dev/sda2  extended             2.6
    /dev/sdsa5  Linux-swap          2.6
However, fdisk shows the following
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb74510e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3433    27575541    7  HPFS/NTFS
/dev/sda2            3434        3784     2819407+   5  Extended
/dev/sda5            3434        3784     2819376   82  Linux swap / Solaris

---

### Post by rreese6 on 2009-09-30
Bob,
I have seen that problem before, where the NTFS partition doesn't want to leave.
Sometimes it is easier to boot the LiveCD, open Terminal
and work through fdisk
since the 80 gig is the only disk it will be the sda drive
so ```
fdisk /dev/sda
```
press "m" for the menu.
Press "p" to list the partitions

Currently it looks like this:

```
Device Boot Start End Blocks Id System
/dev/sda1 * 1 3433 27575541 7 HPFS/NTFS
/dev/sda2 3434 3784 2819407+ 5 Extended
/dev/sda5 3434 3784 2819376 82 Linux swap / Solaris

```

We want it to look somewhat like this:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          22      176683+  83  Linux
/dev/sda2             663         789     1020127+   5  Extended
/dev/sda3              23         662     5140800   83  Linux
/dev/sda5             663         789     1020096   82  Linux swap / Solaris

``` NOTE : your numbers will be different....

so, now back to fdisk.
it would probably be best just to remove all the partitions.
then write and quit
that would give you a blank HD
once that is done click the install icon
and install Ubuntu.
make sure to use entire disk
that should complete everything.

---

