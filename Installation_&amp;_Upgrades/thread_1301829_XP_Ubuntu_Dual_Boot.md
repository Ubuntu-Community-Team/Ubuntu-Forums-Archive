---
title: "XP Ubuntu Dual Boot"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by mjulius on 2009-10-26
Hi -

I have an older Dell Dimension 4600 that I would like to dual boot XP and Ubuntu 9.04.
I have 2 hard drives (both western digital 40 GB), one with XP Pro, and the other with Ubuntu 9.04. After I installed Ubuntu, and restarted, I got the Grub Error 21. So, I flipped the hard drives, and now am getting Error 13 when trying to boot to XP. Ubuntu boots just fine.

---

### Post by freecru on 2009-10-26
Did you change the hd#,# in your /boot/grub/menu.lst? If you're pointing to the wrong disk/partition it will throw that error. See here: [http://ubuntuforums.org/showthread.php?t=282545](http://ubuntuforums.org/showthread.php?t=282545) I'm not sure how you have the disks master/slaved so I can't be any more specific.

---

### Post by mjulius on 2009-10-26
Ok - tried that and now I am getting error 21 when trying to boot into xp.

---

### Post by xtjacob on 2009-10-26
You could try the Super Grub Live CD: [http://en.kioskea.net/faq/sujet-4313-super-grub-disk-live-cd](http://en.kioskea.net/faq/sujet-4313-super-grub-disk-live-cd)

---

### Post by arrange on 2009-10-26
Could you post the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/") here? (If you don't know how to run the script, [look here]("http://sourceforge.net/docman/display_doc.php?docid=137292&group_id=250055").)

---

### Post by mjulius on 2009-10-26
I just downloaded and burned it to a cd - now I will boot from it and see, although I have no idea what I am looking for LOL

---

### Post by mjulius on 2009-10-26
Now it won't boot at all - Error 21
I give up - defeated

I'll start all over from scratch (although I just spent the last 7 hours installing XP and Ubuntu)

Should I attempt the Ubuntu install after I install XP, or will it be a waste of time again?

---

### Post by arrange on 2009-10-26
If you had given us more info on the installation (the boot_info_script is a great way of doing this, it's very comprehensive) it could be quite easy to help you.

[COLOR="Silver"]Should I attempt the Ubuntu install after I install XP[/COLOR]
It's the recommended procedure I think.

---

### Post by stlsaint on 2009-10-26
see here for [dualbooting]("http://gwos.org/udsf/doku.php/core:dualbooting:ubuntu") help.

---

### Post by mjulius on 2009-10-26
arrange - I would have tried the script -  but I can't get it to boot anyhow. Also, the link you supplied is no longer available.

Thank you all for your help - I'm just getting to frustrated right now.

---

### Post by jheaton5 on 2009-10-26
Just install ubuntu.  DON'T change the physical positions of the drives.  The installer will read which drive Windows is on.  Install ubuntu to the other drive.  Grub should recognize both OS's and provide the correct codes to boot from the grub menu.  You must have done something wrong the first time.

---

### Post by mjulius on 2009-10-26
In the process of installing XP. When complete, I'll plug the other hard drive in. Both hard drives will be set at Cable select. Then I'll attempt to install Ubuntu. 
Keeping my finger crossed ........

---

### Post by jheaton5 on 2009-10-26
You probably don"t need to install windows again.  But do what you want.

---

### Post by mjulius on 2009-10-26
I didn't know that - I figured I had to because it wouldn't boot. It was giving me error 21. 
Windows is now installed on one of the hard drives, now I will attempt the Ubuntu install on the other drive - hopefully I'll do it right this time.

---

### Post by jheaton5 on 2009-10-26
Relax, go slow and read everything before you make a selection.

---

### Post by mjulius on 2009-10-26
Ok -  I am running 2 hard drives

Do I select "Install them side by side, choosing between them each start-up"
or do I select "use the entire disk" and selecting the blank hard drive?

---

### Post by jheaton5 on 2009-10-26
Select use entire disk, but make sure you have the correct disk selected.

---

### Post by jheaton5 on 2009-10-26
I'm going off line now, but I will be back on line in about 3 hours.  Hopefully all will go well.;)

---

### Post by mjulius on 2009-10-26
It's installing - I've done everything the same way as before, which is starting to make me sweat :)

I'll post as soon as this is complete in about 10 minutes.

---

### Post by mjulius on 2009-10-26
The Ubuntu install is complete. Restarted the computer, and it gives me the same error as before. "Error 21"

XP Pro is installed on the primary drive, and Ubuntu is installed on the secondary drive, but I can't access either.

---

### Post by oldfred on 2009-10-26
When you do the install do you have both drives installed? Do you let it install grub to the first drive? Error 21 says it is looking for a drive that does not exist. The script which you can run from the liveCD tells us what is wrong with your install

error 21
[http://members.iinet.net.au/~herman546/p15.html#21](http://members.iinet.net.au/~herman546/p15.html#21)

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by mjulius on 2009-10-26
Thanks oldfred - 
I am booting the liveCD right now - I'll post back soon

p.s. Yes both drives are installed during the Ubuntu install, but it never asked me anything about grub.

---

### Post by mjulius on 2009-10-26
Here are the results:


```
 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x708ba94c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,108,029    78,107,967   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x427b427a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    75,184,199    75,184,137  83 Linux
/dev/sdb2          75,184,200    78,156,224     2,972,025   5 Extended
/dev/sdb5          75,184,263    78,156,224     2,971,962  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="96B834DFB834C013" TYPE="ntfs" 
/dev/sdb1: UUID="bdde7f26-b355-4cdb-8d8c-8c6a77dde0bb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="b724cc59-c0ec-431b-863a-33a11115e078" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=bdde7f26-b355-4cdb-8d8c-8c6a77dde0bb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bdde7f26-b355-4cdb-8d8c-8c6a77dde0bb

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        bdde7f26-b355-4cdb-8d8c-8c6a77dde0bb
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=bdde7f26-b355-4cdb-8d8c-8c6a77dde0bb ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        bdde7f26-b355-4cdb-8d8c-8c6a77dde0bb
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=bdde7f26-b355-4cdb-8d8c-8c6a77dde0bb ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        bdde7f26-b355-4cdb-8d8c-8c6a77dde0bb
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=bdde7f26-b355-4cdb-8d8c-8c6a77dde0bb /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b724cc59-c0ec-431b-863a-33a11115e078 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================

``````

```

  19.7GB: boot/grub/menu.lst
  19.7GB: boot/grub/stage2
  19.7GB: boot/initrd.img-2.6.28-11-generic
  19.7GB: boot/vmlinuz-2.6.28-11-generic
  19.7GB: initrd.img
  19.7GB: vmlinuz

---

### Post by mjulius on 2009-10-26
It looks like Grub is installed, but is it in the right place?

---

### Post by mjulius on 2009-10-26
Any Ideas? Anyone?

---

### Post by arrange on 2009-10-26
So, to sum up: when you reboot, you see something like this:```
        Ubuntu 9.04, kernel 2.6.28-11-generic
        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
        Ubuntu 9.04, memtest86+
        Other operating systems:
        Microsoft Windows XP Professional
```

Whatever you choose, it gives you Error 21. In BIOS you can see both disks, and booting is set to start from **sda**(the Win disk). Is that right?

---

### Post by mjulius on 2009-10-26
No - I don't even see that - it just say's Error 21

---

### Post by oldfred on 2009-10-26
I do not see anything wrong, perhaps someone else will.

Grub is in the MBR of sda which should be the first drive and it looks to the ubuntu install in sdb1 which has the grub stage2 and menu.lst
The menu.lst looks correct. Do you get this far or is the error before grub presents the menu? The menu looks correct for both Ubuntu and windows, have you tried both?

---

### Post by mjulius on 2009-10-26
I can't even get that far to select either OS. When I restart the machine, it instantly goes to Error 21

---

### Post by mjulius on 2009-10-26
Also - only one hard drive is showing up in the BIOS

---

### Post by xtjacob on 2009-10-26
That could be it... Which hard drive is it?

---

### Post by oldfred on 2009-10-26
Never mind my previous post you had already answered it before I posted.

Is this a very old computer that required the boot to be at the beginning of the harddrive?

The post I gave to Herman's site shows various grub error screens, are you getting error 21 or something else?

---

### Post by mjulius on 2009-10-26
xtjacob - I'm not sure which drive it is because both drives are identical.


oldfred - it's a Dell 4600 - 2.4Gh P4 - 1 GB RAM - 2 (40 GB Western Digital) Hard drives

---

### Post by xtjacob on 2009-10-26
Is it possible that grub finds part of it's self but not the other part so it just spits out error 21?

---

### Post by mjulius on 2009-10-26
Beats me - I have reinstalled both Operating Systems twice today with no luck. 

I think it is safe to assume that you cannot dual boot a Dell 4600 with XP and Ubuntu.

---

### Post by mjulius on 2009-10-26
I will try this again tomorrow. I have spent the entire day messing with this. 

Thank You everyone!

---

### Post by arrange on 2009-10-26
Make sure the second HDD is not disabled in BIOS. Otherwise Grub won't be able to see it too.

---

### Post by oldfred on 2009-10-26
I saw syslinux in the MBR of sdb?  I would try reinstalling grub to both sda (hd0) and to sdb (hd1) and try booting with just sdb installed. If the drives are still set up as per the script the find command should give (hd1,0) but run that just to be sure.

from a terminal session in the live CD:

sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd1,0)
root (hd1,0) #use the numbers from the previous command if different
setup (hd0)
setup (hd1)

---

### Post by jheaton5 on 2009-10-26
I'm back.  You've been a busy bee.

I recall that you installed windows when only one drive was connected.  Then you connected the second drive and installed ubuntu.  Is this correct?

You reported that your BIOS only sees one drive.  Is this when both drives are connected?  The fact that you were able to install ubuntu on sdb indicates that both drives are being seen.

I don't see anything wrong in your boot information.  If you decide to reinstall everything, wipe both disks and then install windows first and ubuntu second with both drives hooked up during both installs.

The installer does not mention grub unless you choose Advanced at step 7.  I see no reason for you to do that.

---

### Post by jheaton5 on 2009-10-26
[Read this thread]("http://ubuntuforums.org/showthread.php?t=62717")

---

### Post by mjulius on 2009-10-27
Was up all night waiting for the arrival of my new granddaughter, and had plenty of time to read and try all the suggestions you all gave me, with no luck. 


Ok -I have solved the problem. I removed both (40 GB) hard drives, cussed a bit, drank a little coffee. I then installed an 80 GB hard drive. I installed XP Pro first, then installed Ubuntu. No problem. 

Solution: get rid of 2 hard drives and use one instead on a Dell Dimension 4600. 

Thank You All for your input! :)

---

### Post by jheaton5 on 2009-10-27
Great news.  How is mother and child?  Aren't grandchildren great?

---

### Post by mjulius on 2009-10-27
So far so good - she hasn't delivered yet - but it's close :)

Although I think I am still too young to be a grandpa (39), it's going to be fun spoiling that little girl. Oh yes, I said spoil, it's time for a little payback with my daughter LOL! 

Have a great day!!

---

