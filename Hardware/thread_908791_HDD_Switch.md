---
title: "HDD Switch"
date: 2008-09-02
forum: Hardware
---

### Post by philgenius on 2008-09-02
Hi. I have a 400 GB external HDD with Ubuntu on an extended partition.

I have a 60 GB internal HDD in a Thinkpad T60 with Windows XP on it.

My plan is to swap the entire 50 GB Windows partition on to the external HDD (the other partition has ThinkVantage utilities on it, Rescue & Recovery and whatnot), then shrink the /home partition down to a manageable size and shift everything Ubuntu to the internal hard drive. I want Windows to still work if I boot off of the external.

All this is to make Ubuntu more mobile. Every time I boot up, I'm locked to a power outlet.

Any idea on how to do this?

---

### Post by falcon61102 on 2008-09-02
As far as the copying and all goes, that shouldn't give you any trouble but you may run into problems from Windows.  Microsoft didn't design windows to be mobile and it has problems with being on an external drive.  One of the problems stems from the fact that Windows was designed to be the first drive on the computer and often times will give you errors when it's not.  Also, because of security issues, it may also give you trouble.

An option you could do is clean up the Windows partition so that it does not occupy as much space on the internal HD as it normally does and install Ubuntu onto the internal drive as a dual boot.  You should have enough space to have both OS's plus other software installed and then if you need more space you always have the external.

---

### Post by philgenius on 2008-09-03
Now Windows won't boot for whatever reason.

Now I simply want to get all my files and settings over to the internal drive. That includes custom color editing on the Ubuntu Human theme (instead of orange, gunmetal gray). I also want to ex/import my other custom settings, like my 3D desktop and such. Any good backup/restore programs that transfer EVERYTHING? (yes, everything. period.)

---

### Post by falcon61102 on 2008-09-03
Alright, walk me through exactly what you did so that we can determine what the error is.

---

### Post by philgenius on 2008-09-03
That's just it. I don't know what happened. I haven't booted into Windows for weeks. Now I want to trash Windows completely and have Ubuntu with all of my exact settings on the internal drive.

---

### Post by falcon61102 on 2008-09-03
What did you copy and where did you copy it?  Also, I realize Windows isn't booting, but is Ubuntu still booting?

---

### Post by philgenius on 2008-09-03
I haven't copied anything yet. I am still typing from Ubuntu.

---

### Post by falcon61102 on 2008-09-03
Ok, if I understand correctly, now you wish to get rid of windows all together and just use Ubuntu?  
And right now you Ubuntu installation is currently on an External HD and you want to move that to the internal one on your laptop?
And do you want to back up everything that is currently on the internal drive or just get rid of it?

---

### Post by philgenius on 2008-09-03
I wish to do away with Windows and shift Ubuntu to the internal drive. With all settings intact as illustrated in my second post in this thread.

---

### Post by falcon61102 on 2008-09-03
Check this thread out.  It's a similar situation.  And all the settings will stay intact.

[http://ubuntuforums.org/showthread.php?p=5721791](http://ubuntuforums.org/showthread.php?p=5721791)

---

### Post by philgenius on 2008-09-04
Thanks.


When the copying is all said and done, I check the partitions with GParted on the LiveCD and apparently the commands did not copy all the data. Gparted says:
```

/dev/sdc6= 149.01 MiB  Used: 28.21 MiB   /boot   |
/dev/sdc7= 24.42 GiB   Used: 4.69 GiB    /       |-->External Drive
/dev/sdc8= 19.66 GiB   Used: 7.92 GiB    /home   |

/dev/sda6= 172.54 MiB  Used: 10.98 MiB   /boot   |
/dev/sda8= 20.04 GiB   Used: 333.83 MiB  /       |-->Internal Drive
/dev/sda7= 26.24 GiB   Used: 383.02 MiB  /home   |

```
Here are the commands I used:

```
ubuntu@ubuntu:~$ sudo dd if=/dev/sdc6 of=/dev/sda6
305172+0 records in
305172+0 records out
156248064 bytes (156 MB) copied, 30.7749 s, 5.1 MB/s
ubuntu@ubuntu:~$ sudo dd if=/dev/sdc8 of=/dev/sda7
41238792+0 records in
41238792+0 records out
21114261504 bytes (21 GB) copied, 2321.98 s, 9.1 MB/s
ubuntu@ubuntu:~$ sudo dd if=/dev/sdc7 of=/dev/sda8
dd: writing to `/dev/sda8': Input/output error
42025977+0 records in
42025976+0 records out
21517299712 bytes (22 GB) copied, 2309.14 s, 9.3 MB/s
ubuntu@ubuntu:~$ 

```

Any idea why?

---

### Post by falcon61102 on 2008-09-04
Based on the commands that you used, it copied all the data.  gparted may not be reading the partitions correctly.  Have you examined the partitions with Nautilus (File Browser) to see if the files are all there or at least it looks like all the files are there?  It may be that gparted is only reading the first layer of the folders and not scanning all the files.

Part of your problem may also be that you attempted to copy sdc7 to sda8 and sdc7 is a larger partition than sda8.

---

### Post by philgenius on 2008-09-04
Nautilus reveals absolutely no files in the copi-ee partitions. Would CloneZilla be helpful? How do I operate it?

---

### Post by falcon61102 on 2008-09-04
There are numerous copy/image utilities out there, but unfortunately I don't really have experience with them, not in Ubuntu anyway.  Sorry.

---

### Post by philgenius on 2008-09-05
After using your first suggestion after modifying the partitions to be of the exact same size, I tried to reconfigure GRUB. BTW, the partition swapping was a success this time. Checked using GParted and Nautilus.

I first editted the menu to fit my settings (including root=UUID=... which I put the / partition's UUID) then ran the following commands in LiveCD:

```

$ sudo grub 
> find /grub/stage1
(hd0,1)
> root (hd0,1)
> setup (hd0)
> *awholebunchofoutputsthatendwithasuccessnotification*
> quit
> reboot

```

So then I rebooted, but when I selected Ubuntu from the menu in GRUB, the laptop rebooted instead of switching to Ubuntu. What happened?

---

### Post by falcon61102 on 2008-09-05
Something must not have gone right with the GRUB.  If possible, boot up with your LiveCD and run the GRUB commands again.  Something to watch is after you run the setup (hdX) command, the output should end in success but it should also not have any "Fail"'s listed.  If you see Fail anywhere in there it's not going to work and something needs to be adjusted.  If that happens, post your menu.lst and I'll take a look at it.

---

### Post by philgenius on 2008-09-05
Here is my output of the GRUB commands:
```

$ sudo grub
> find /boot/grub/stage1

Error 15: File not Found

> find /grub/stage1
 (hd0,1)
> root (hd0,1)

> setup (hd0)]
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"... 16 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0) 1+16 p (hd0,1)/grub/stage2 /grub/menu.lst"... succeeded
Done.

```

And the menu.lst:

```

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd1,5)/grub/splashimages/Linux.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=1e0a5cc2-982a-480e-b69f-02b37cf12136 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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
# defoptions=quiet

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=1e0a5cc2-982a-480e-b69f-02b37cf12136 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=1e0a5cc2-982a-480e-b69f-02b37cf12136 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+-noncdboot
root		(hd0,1)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

```

The "root=UUID="'s are the UUID's of the root partition.

---

### Post by falcon61102 on 2008-09-05
I'm not sure why your GRUB is installed to /grub when it should be /boot/grub but you're still getting to the GRUB menu when you boot so it must not be affecting anything.

Anyway, add /boot before the kernal and initrd strings so that they look like this:
```
/boot/vmlinuz...
```

---

### Post by philgenius on 2008-09-05
I believe that /boot directory is in the /home partition. The actual /boot partition only has /grub.

---

### Post by falcon61102 on 2008-09-05
That's right, I forgot you are using a boot partition.  Ok, the problem is more than like with the GRUB being confused about where to looke for the kernal files.  You're probably going to have to change the root line as well as put /boot in front of the kernal and initrd lines.  Post the results from:
```
sudo fdisk -l
```
And we'll see if we can't make some sense of it.

---

### Post by philgenius on 2008-09-05
Here ya go:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         657     5277321   82  Linux swap / Solaris
/dev/sda2             658         676      152617+  83  Linux
/dev/sda3             677        3864    25607610   83  Linux
/dev/sda4            3865        6431    20619427+  83  Linux
ubuntu@ubuntu:~$ 

```

---

### Post by falcon61102 on 2008-09-05
It looks like you need to change your menu.lst from
```
root (hd0,1)
```
To:
```
root (hd0,2)
```

And make sure that you add the /boot before the kernal file.

---

### Post by philgenius on 2008-09-06
Done.

And it still does not work.

Here is my menu.lst as of now:
```

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd1,5)/grub/splashimages/Linux.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=1e0a5cc2-982a-480e-b69f-02b37cf12136 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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
# defoptions=quiet

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1e0a5cc2-982a-480e-b69f-02b37cf12136 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1e0a5cc2-982a-480e-b69f-02b37cf12136 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+-noncdboot
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
##title		Other operating systems:
##root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

```

BTW, the (hd0,2) partition refers to the root partition, which does have a /boot folder but has absolutely nothing in it.

---

### Post by philgenius on 2008-09-06
*post deleted*

---

### Post by falcon61102 on 2008-09-06
Is it giving you any errors?  What is it doing?

---

### Post by philgenius on 2008-09-06
Simply restarting upon menu select, as always. No errors.

---

### Post by falcon61102 on 2008-09-06
You mentioned earlier that the boot partition may be in your /home partition.  Normally it's in the Root partition "/" and that's what it is setup for right now.

To test if it's in the /home partition, you need to change two values in the menu.lst.
root (hd0,2) to root (hd0,3).  

Also, you would need to update the UUID for those entries to match your /home partition.  You can get the UUID with:
```
sudo blkid
```

---

### Post by philgenius on 2008-09-06
Everything is in the /boot partition, not /boot folder. Despite the fact that the /home partition does not have a /boot folder, I will attempt your suggestion.

---

### Post by falcon61102 on 2008-09-06
What you need to find are where you kernal and initrd files are on your system.  They may have been moved around a bit when you switched the partitions.  Once you locate those files, you will be able to direct the menu.lst to load those files and it should boot.

---

### Post by philgenius on 2008-09-06
There are right outside of the /grub folder, in the /boot partition.

---

### Post by falcon61102 on 2008-09-06
Try directing your menu.lst to load those locations and see if that gives you some results.  Also, one thing I also noticed in you fdisk -l there is no partition flagged as a boot partition.

---

### Post by philgenius on 2008-09-06
That would figure. I thought I editted my fstab, but it had remained the same, pointing to the external drive that was never connected.

---

### Post by philgenius on 2008-09-06
Despite the fstab editting, an attempt at booting always ends up as a reboot.

---

### Post by philgenius on 2008-09-06
When I use the install function from the liveCD to "install" Ubuntu, when I get to the partitioner, it does not recognize the partitions on the internal disk as mount points. Is that a problem? (For example, sda3 is not recognized as /.)

---

### Post by philgenius on 2008-09-06
New progress:

I reinstalled standard Ubuntu on the internal drive and booted into the external. I then dd copied the / and /home partitions, but not the /boot partition, keeping the default settings intact. I also editted the fstab file that was copied over. Now GRUB boots, Ubuntu loads, but just hangs at the "bouncing bar" screen. Why?

---

### Post by falcon61102 on 2008-09-06
Did you change the UUID's in the fstab?

---

### Post by Hellkeepa on 2008-09-06
HELLo!

Use ALT + F1 to see where it hangs, or to monitor the boot process.
You can press this combination at any time after the boot-splash first appears.

Happy surfin'!

---

### Post by philgenius on 2008-09-06
Falcon61102--- Yes, I did edit the UUID's using blkid.

Hellkeepa--- This is what I got: 
```

Starting up ...
Loading, please wait ...

```

And it hangs from there.

---

### Post by falcon61102 on 2008-09-06
If all the UUID's are correct for all the partitions try booting up in the recovery mode if you haven't done so yet.  It may be an unrelated problem.

I'm curious, if you reinstalled why did you copy your old root partition over the new?

---

### Post by philgenius on 2008-09-06
I had custom coloring that was a **pain** to configure and I really did not want to do that again. Also, I really did not want to reinstall all the plugins and software that I already had.

And about that recovery mode, I looked around online and found the fsck -y command. But the system hangs on 
```

[  19.740409] Uniform CD-ROM Driver revision: 3.20

```

And the output that it hangs on seems to vary with each boot (last time it hang on some USB output). Due to this hang, I cannot input any commands.

---

### Post by falcon61102 on 2008-09-07
I'm not sure exactly how to go about this, but you may be able to backup your coloring and whatnot so when you reinstall you can restore it.  It's just a guess, but I believe that is all in the /home directory which I'm sure you're going to want to back up anyway.  

As far as the plugins go, I know it's a pain to reinstall them but you have to weigh the time it's going to take to fix this, if possible, against how much time it would be to install a few plugins.

---

