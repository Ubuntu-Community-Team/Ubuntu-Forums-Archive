---
title: "Unable to boot into XP and not able to see NTFS files in Ubuntu"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by newbie_ub on 2009-03-03
HI all before installing Ubuntu i had 4 drives namely:
C: Drive (NTFS) - Windows XP SP2 installed in it and important program files
D: Drive (FAT32) - Some Important Files
E: Drive (NTFS) - Some Important Files
F: Drive (NTFS) - Free Space

So, i installed ubuntu 7.10(as i didn't get 8.10 live CD yet, i will get it soon, i can't download the .iso of 8.10 so i installed 7.10) in my F: Drive. Installation went smoothly.

After installing, i am not able to boot into windows XP. I don't get the option while starting up to boot into XP or Ubuntu. It asks to press Esc. but i don't see any option of XP there.:(

Also, i am unable to see my C: Drive and E: Drive(both NTFS) files on ubuntu. I am only able to see D: Drive(FAT32) in ubuntu. 
One of my online freind who is good at ubuntu told me to write some commands in terminal window to see if i have C: and E: Drives in my hard disk. And thankfully, it was there, but not able to see in Ubuntu.

Please, i want to boot into XP and don't want to lose any data:( Help me please. I am a complete novice in Ubuntu/Linux.

---

### Post by newbie_ub on 2009-03-03
**_Additional Info:_**
[COLOR="Red"]
This is what i got when i did  sudo fdisk -l[/COLOR] 

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a1e6d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1153     9261441   83  Linux
/dev/sda2            1276        4869    28868805    f  W95 Ext'd (LBA)
/dev/sda3            1154        1275      979965   82  Linux swap / Solaris
/dev/sda5            1276        2550    10241406    b  W95 FAT32
/dev/sda6            2551        3825    10241406    7  HPFS/NTFS
/dev/sda7            3826        4869     8385898+   7  HPFS/NTFS

Partition table entries are not in disk order

============================================================================================

[COLOR="Red"]And this is what i got when i did sudo cat /boot/grub/menu.lst in terminal window[/COLOR]

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
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# root          (hd0,1)
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
# kopt=root=UUID=736a5e0d-0d15-4786-a2d2-4b5e6ab81ec1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=736a5e0d-0d15-4786-a2d2-4b5e6ab81ec1 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=736a5e0d-0d15-4786-a2d2-4b5e6ab81ec1 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Rallg on 2009-03-03
EDITED

What I originally wrote here would not have worked - the above partition list had not been posted while I was typing it.

---

### Post by newbie_ub on 2009-03-03
> **Rallg said:**
> EDITED

What I originally wrote here would not have worked - the above partition list had not been posted while I was typing it.

Yeah Rallg, i tried that i got 
Error 13: Invalid or unsupported executable format. Press any key to continue

Then there was an option of 
Windows XP
Ubuntu 7.10, Kernal 2.6.22-14-generic
Ubuntu 7.10, Kernal 2.6.22-14-generic(recovery mode)
Ubuntu 7.10, memtest 86+

Since, it is not working, shall i open that command again in terminal window and change it to what it was before ? Please tell that command again if i need to change it back since u edited the post.

---

### Post by Rallg on 2009-03-03
You can remove the added info from menu.lst (the part I edited away, above). It would normally be there by itself, lower down the file, if your system was OK.

If I understand your fdisk output correctly, it means that you installed Ubuntu to your hard drive's first partition (where C: was), rather than to where F: was. If so, that is bad news. Also, it appears that Windows is on an extended partition - don't know how it got there.

Your situation is complicated and requires expertise above my head.

Possibly, the situation can be fixed by booting to live Ubuntu (on CD or USB), then using the partition editor program. Maybe you can remove the offending installation of Ubuntu (at the start of the hard drive), then get Windows assigned as a boot-flag primary partition. If that works (I doubt it), you may be able to boot to the Windows install CD (if you have it), and restore the master boot record. If that works, you will have Windows but not Ubuntu.

If that does not work, then you may have to copy out all your valuable stuff to backup media, then re-install Windows.

But as I said, it is above my head.

---

### Post by cariboo on 2009-03-03
From the output of sudo fdisk -l, it looks like you overwrote your Windows partition. That is why it is not showing up in the /boot/grub/menu.lst. You still have the two partitions that you say have important files on them though. 

Hopefully you made backups before changing anything.

Jim

---

### Post by newbie_ub on 2009-03-03
No buddy, i didn't overwrote ubuntu over my windows. 

[COLOR="Red"]According to my sudo fdisk -l  output, let me tell you which drive is it according to windows: [/COLOR]

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a1e6d37

Device Boot Start End Blocks Id System
/dev/sda1 * 1 1153 9261441 83 Linux
/dev/sda2 1276 4869 28868805 f W95 Ext'd (LBA)
/dev/sda3 1154 1275 979965 82 Linux swap / Solaris
/dev/sda5 1276 2550 10241406 b W95 FAT32    [COLOR="Red"]<<-- D: Drive ( Can be see in Ubuntu - FAT32)[/COLOR]
/dev/sda6 2551 3825 10241406 7 HPFS/NTFS    [COLOR="Red"][COLOR="Red"]<<-- E: Drive ( Cannot be seen in Ubuntu - NTFS)[/COLOR][/COLOR]
/dev/sda7 3826 4869 8385898+ 7 HPFS/NTFS    [COLOR="Red"]<<-- C: Drive  ( Cannot be seen in ubuntu - NTFS)[/COLOR]

So, files are there, but not able to see the NTFS files in Ubuntu. Please help me out.

---

### Post by Rallg on 2009-03-03
Now that we have a clearer idea of your partitions...

In live Ubuntu (USB or CD) open the partition editor, select sda7, manage flags, mark it as boot.

Then try adding the Windows chainloader code (which you already know) to the grub (on hard drive) menu.lst, using root=(hd0,6). Or, try (hd0,5).

For booting to Windows, it matters whether grub (rather than all of Ubuntu) can see the Windows partition.

Not sure if Windows allows itself to boot from an extended partition, which is where you seem to have it.

---

### Post by newbie_ub on 2009-03-03
Hello Rallg
I have Ubuntu Live CD and in that i can see folders like - [COLOR="SeaGreen"]bin, casper, disctree, dists, install, isolinux, pics, pool, preseed, programs, ubuntu, autorun.inf, md5sum.txt, README.diskdefines, start.bmp, start.exe, start.ini, ubuntu.ico, wubu-cdboot.exe. [/COLOR]

I can't see "partition editor".

Also,please tell me the code again, i don't know. I am completely a newbie to linux/ubuntu. 

Can you tell it step by step of what i should do/approach ?

Bear wih me.

Thanks

---

### Post by newbie_ub on 2009-03-04
Please help me out someone ?:(

---

### Post by newbie_ub on 2009-03-04
[COLOR="Red"]This is what i got when i wrote df in terminal window[/COLOR]

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              9115960   2080916   6571972  25% /
varrun                  257056        88    256968   1% /var/run
varlock                 257056         0    257056   0% /var/lock
udev                    257056        76    256980   1% /dev
devshm                  257056         0    257056   0% /dev/shm
lrm                     257056     34696    222360  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda5             10231392   9870264    361128  97% /media/sda5
/dev/scd0               712508    712508         0 100% /media/cdrom0

Please, help me to boot into XP :(

---

### Post by newbie_ub on 2009-03-04
Now, i corrected one of the problems. I am able to see all my drives(both NTFS and FAT) in ubuntu.
But, i am still not getting the option to boot into XP at startup. Please help me out. 
Why noone is replying to me ? :(

---

### Post by Rallg on 2009-03-04
Keep in mind that many of us are not in your time zone, and in any case are not on the forum all the time.

When you looked at the file system (a couple of posts ago), you were looking at the file system of the live USB, not the file system on your hard drive.

Start the live USB. Then, go to the System menu, Administrative Tools, Partition Editor.

After the Partition Editor loads, it will show how each device is partitioned (not just the hard drive). Look in the upper right corner of the editor. You will see a place where you can choose which device is displayed. Be sure that you choose the hard drive. You will know you have the correct choice when the expected partitions appear in the display area.

Look at the partition that has XP. How is it labeled? Probably it is sda7 (from your prior post). Whatever it is, write that down for future use.

Right-click that partition, and when the context menu appears, choose manage Flags. Select the boot flag (might also need lba, not sure). That action will also remove the existing boot flag from your sda1 partition, which won't hurt here (because you are already hurting).

Close the partition editor. Mount the hard drive into the live Ubuntu. Go to the partition where you have installed Ubuntu on the hard drive (NOT the USB). If you see files and folders labeled "casper" and "autorun" then you are in the USB file system, which is the wrong place. You should see a file system with bin, boot, and numerous other folders.

Open the boot folder. Within it, open the grub folder. Find the menu.lst file. Save a copy of the file where you will be able to find it later, in case you need to restore it.

Double-click the menu.lst file. You want to edit it (display it). This is where you will put the boot instructions for Windows. In the menu.lst file there is model code for Windows, commented out. Copy that code, paste it just under End Default Options, and remove the hash symbols (so that the pasted code is not a comment).

The catch is that in your system, Windows is on the sda7 partition, which is the same as (hd0,6) partition. Modify the Windows boot instruction set, by changing root (hd0,0) to root (hd0,6). Save the modified file.

Then, attempt to boot normally.

If that does not work, then I am running out of ideas.

---

