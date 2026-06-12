---
title: "Unable to dual boot Ubuntu and Windows 7"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by tformed on 2009-05-20
Hi,

I'm new to Ubuntu and wish to learn more about it, so I decided to free up some space in my hard drive and do an install of Ubuntu. I've tried dual booting Ubuntu and Vista originally, and got tired of getting it to dual boot properly.

Anyway, I installed Ubuntu using the (use largest continuous free space option), and now I am able to boot up Ubuntu just fine. On boot up, I do see Windows 7 on the Grub list, but when I select it, my laptop just restarts and goes back to Grub Option Screen.

I apologize if there are threads already made for this, I have been searching through the internets but wasn't able to find a solution to this problem. 

As a reminder, I am new to Ubuntu, and new to terminal commands. (*reading more about using the terminal ;)* )

Thanks in advance. :KS

---

### Post by presence1960 on 2009-05-20
unfortunately you are going to have to use the terminal, but this is a good thing as you will learn to be comfortable with it. Open a terminal by going to Applications > Accessories > Terminal. Paste this command in terminal > sudo fdisk -l BTW that is a lowercase L. Press Enter, when prompted type your password. This will produce text output. paste the output back here please so we can see what your partitions setup looks like.

---

### Post by lindsay7 on 2009-05-20
Lets see what you drive or drives look like

Type this in the terminal which you can find under applications/accessories in the menu at the top of the desktop screen.

"sudo fdisk -l" do not put in the quotation marks and that is a letter l nto the number 1.  Copy and post the results here.

---

### Post by tformed on 2009-05-20
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5335872d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        9556    76653568    7  HPFS/NTFS
/dev/sda3            9557       12161    20924662+   5  Extended
/dev/sda5            9557       12047    20008926   83  Linux
/dev/sda6           12048       12161      915673+  82  Linux swap / Solaris



as a side note, the ubuntu partition should be about 20 gigs and the Windows partition about 70gigs.

---

### Post by presence1960 on 2009-05-20
open a terminal and type > gksu gedit /boot/grub/menu.lst That is a lowercase L in .lst

This will open your menu.lst file. scroll down to the bottom and edit your Windows entry to look like this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 7
rootnoverify	(hd0,0)
chainloader	+1
```

Click save at top of window, close the window and reboot and see what happens when you choose windows. If you already have that entry EXACTLY for windows let us know.

---

### Post by tformed on 2009-05-20
Ok,

it was like this before:


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

and after the edit,


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows 7
rootnoverify    (hd0,0)
chainloader    +1

_______________________________________________________________________________

I saved it, and restarted the computer. The ASUS logo comes up as usual, followed by the option to select the OS. I selected Windows 7 and the computer just restarted and it came back up to the Grub menu screen.

---

### Post by presence1960 on 2009-05-20
well on the positive side you are moving along pretty well with using terminal. I hate to do this to you, but to get a better look at your setup can you download to your Desktop the Boot Info Script from here : [http://sourceforge.net/projects/bootinfoscript](http://sourceforge.net/projects/bootinfoscript)

Then open a terminal and run > sudo bash ~/Desktop/boot_info_script*.sh

This will create a RESULTS.txt file on your Desktop. Copy the contents of that file and paste in here. Then highlight all text and click # on the toolbar please.

---

### Post by damis648 on 2009-05-20
Would you mind trying to change the text to
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista (loader)
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1
```

This may fix it, based on the size of the partitions I would guess this is meant to be the bootable volume?

---

### Post by presence1960 on 2009-05-20
> **tformed said:**
> Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5335872d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        9556    76653568    7  HPFS/NTFS
/dev/sda3            9557       12161    20924662+   5  Extended
/dev/sda5            9557       12047    20008926   83  Linux
/dev/sda6           12048       12161      915673+  82  Linux swap / Solaris



as a side note, the ubuntu partition should be about 20 gigs and the Windows partition about 70gigs.

I just noticed what you said about the size of your windows partition. The 70 GB partition is sda2. Maybe you can change the Windows entry in menu.lst to (hd0,1) not (hd0,0)

---

### Post by tformed on 2009-05-20
Here we go:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5335872d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   153,513,983   153,307,136   7 HPFS/NTFS
/dev/sda3         153,517,140   195,366,464    41,849,325   5 Extended
/dev/sda5         153,517,203   193,535,054    40,017,852  83 Linux
/dev/sda6         193,535,118   195,366,464     1,831,347  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3A1011231010E821" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="FC4822D748229086" TYPE="ntfs" 
/dev/sda5: UUID="7ef07a2a-9ad0-464b-9244-6568278fd13d" TYPE="ext3" 
/dev/sda6: UUID="70ea9fef-f247-405e-8550-66db0a8fb5a2" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/robert/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=robert)


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7ef07a2a-9ad0-464b-9244-6568278fd13d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7ef07a2a-9ad0-464b-9244-6568278fd13d

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
uuid        7ef07a2a-9ad0-464b-9244-6568278fd13d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7ef07a2a-9ad0-464b-9244-6568278fd13d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        7ef07a2a-9ad0-464b-9244-6568278fd13d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7ef07a2a-9ad0-464b-9244-6568278fd13d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        7ef07a2a-9ad0-464b-9244-6568278fd13d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows 7
rootnoverify    (hd0,0)
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=7ef07a2a-9ad0-464b-9244-6568278fd13d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=70ea9fef-f247-405e-8550-66db0a8fb5a2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  86.3GB: boot/grub/menu.lst
  86.4GB: boot/grub/stage2
  86.2GB: boot/initrd.img-2.6.28-11-generic
  86.3GB: boot/vmlinuz-2.6.28-11-generic
  86.2GB: initrd.img
  86.3GB: vmlinuz
```

---

### Post by damis648 on 2009-05-20
Try what I suggested (and presence1960 also), that will likely rectify the situation. If not, we will try other things.

---

### Post by presence1960 on 2009-05-20
I would change the rootnoverify (hd0,0) to rootnoverify (hd0,1) as damis and I suggested.

---

### Post by tformed on 2009-05-20
damis,

I went ahead and tried your suggestion. Unfortunately it yielded the same result. As soon as I selected "Windows Vista (loader)", the computer restarted, and the grub menu came up again. :(

Right now I have it as:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows 7 (loader)
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1

I changed the title to Windows 7. XD

---

### Post by presence1960 on 2009-05-20
> **tformed said:**
> damis,

I went ahead and tried your suggestion. Unfortunately it yielded the same result. As soon as I selected "Windows Vista (loader)", the computer restarted, and the grub menu came up again. :(

what is on sda1? it looks way to small to be a recovery partition. Also it is marked as bootable. I suspect this is the root (no pun intended :p) of your problem. Plus there is a problem with that partition not ending on the cylinder boundary.

---

### Post by tformed on 2009-05-20
Since I did a fresh install of Windows 7, I created a ~70gig partition for it. Windows 7 automatically created ~10mb partition for system/recovery files, I think it was.

Also, when I had Vista installed before and tried dual booting Ubuntu, I would get the same result, where it would restart, and I'm positive that at that time that partition(the 10mb)  didn't exist.

---

### Post by damis648 on 2009-05-20
> **presence1960 said:**
> what is on sda1? it looks way to small to be a recovery partition. Also it is marked as bootable. I suspect this is the root (no pun intended :p) of your problem.

Hm. What may work (and this is quite a stretch I suppose, but it may just work) is having the Windows install disc fix Windows' MBR, then reinstalling GRUB where perhaps that would fix it. If you have the Windows 7 DVD lying around, boot from it and choose the 'repair' option. It will likely reinstall the windows bootloader to the MBR whereupon the computer will boot directly to 7. You will then need to follow [this]("http://ubuntuforums.org/showthread.php?t=224351") guide in order to reinstall GRUB. It is not an elegant solution, but it just might work.

---

### Post by tformed on 2009-05-20
ok, I'll go ahead and try that.

---

### Post by tformed on 2009-05-20
When I run the repair, it found issues with the startup (as expected), so it corrected the issues and restarted. The weird this is that upon restart, GRUB loaded instead. I'm going to run the repair again just in case.

---

### Post by presence1960 on 2009-05-20
> **tformed said:**
> ok, I'll go ahead and try that.

good luck, something definitely went haywire with the Windows install. I don't like the looks of the info on sda1 or sda2 on your results.txt info you posted. I have to go to bed it is getting late and I have to work tomorrow.

---

### Post by tformed on 2009-05-20
ok, windows repair supposedly found issues and attempted to correct them, and once again upon restart, grub loaded instead of Windows MBR. :(

thank you for your time and help presence and damis. 

I'll take another shot at solving this issue I'm having with dual booting ubuntu and windows again tomorrow morning.

---

### Post by lindsay7 on 2009-05-20
I know you are about to ware out with all of this. I have been keeping up with your trying to fix this.  I you can do this, this will give the best picture of what is going now that you have made some changes.

One more thing to do to make sure you have the windows mbr in place. Boot with you windows install disk and go to the repair option as you did before. I know you ran the repair but that may not have fixed the mbr, so look for the option to get to the command prompt and type "bootrec.exe" then typr bootrec /FixBoot.  That should put the mbr on your system. You should get a response like done or complete if it is successful.

Then do the following if you can.


Ok, I copied this from another post, this will tell what is going on with your drive and what is installed in terms of the mbr and what is in the grub file. This should tell us what is missing and what needs to be done.


Please download this and place it on your Desktop in Ubuntu:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

You will have you run it, so that we can gather more information about your hard drive setup and boot process to troubleshoot the problem more clearly.

After you download it to the Desktop, right-click it and click Properties, then click the Permissions tab and check the box at the bottom of the window that 'allows executing'.

Then click the Applications menu at the top right of your screen, followed by the Accessories menu and then click Terminal. A black window will come up, in it type the following commands, ending each line with a press of the Enter key:

Code:

cd ~/Desktop
sudo ./boot*.sh

Please remember that in Linux, everything is case sensitive. Therefore, a lowercase 'd' is different than an uppercase 'D'. Also, you will be prompted for the password you gave when you installed Ubuntu whenever you use the 'sudo' command. The 'sudo' command escalates privileges and in this case is needed to properly view the hard drives and boot process.

After you have done this, it should place a Results.txt file on your desktop. Double-click that file and select Edit->Copy. Then return here and start a new reply message. In this message, click the # sign at the top of the message editor box and this will give you CODE tags; click between these tags ({code]here[/code}) and paste the contents that you copied from the Results.txt file.

The results should give the direction to take. This should be a fixable problem with out too much to get it done.

---

### Post by presence1960 on 2009-05-21
> **lindsay7 said:**
> 
Then do the following if you can.


Ok, I copied this from another post, this will tell what is going on with your drive and what is installed in terms of the mbr and what is in the grub file. This should tell us what is missing and what needs to be done.


Please download this and place it on your Desktop in Ubuntu:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

You will have you run it, so that we can gather more information about your hard drive setup and boot process to troubleshoot the problem more clearly.

After you download it to the Desktop, right-click it and click Properties, then click the Permissions tab and check the box at the bottom of the window that 'allows executing'.

Then click the Applications menu at the top right of your screen, followed by the Accessories menu and then click Terminal. A black window will come up, in it type the following commands, ending each line with a press of the Enter key:

Code:

cd ~/Desktop
sudo ./boot*.sh



Already done-see post #10

---

### Post by tformed on 2009-05-21
ok when I run the the repair, do I reinstall grub afterwards and post the result of that file? or should I insert the live CD, redownload the file and post the results of the file?

---

### Post by tformed on 2009-05-21
Ok, so I ran FixBoot, and it said it completed successfully. Although there was no changes on boot. So, I tried FixMbr and then Windows 7 booted up automatically, but now I can't view Ubuntu.

So I ran the live CD, and from the terminal, I reinstalled Grub. When I typed the find, it gave me (hd0,4). Grub was reinstalled successfully, after following the steps on the link that was provided. 

If I try to select Windows 7, it just reboots once again. :( I was hoping that would fix it.

Just in case anything has changed:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5335872d

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2    *        206,848   153,513,983   153,307,136   7 HPFS/NTFS
/dev/sda3         153,517,140   195,366,464    41,849,325   5 Extended
/dev/sda5         153,517,203   193,535,054    40,017,852  83 Linux
/dev/sda6         193,535,118   195,366,464     1,831,347  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3A1011231010E821" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="FC4822D748229086" TYPE="ntfs" 
/dev/sda5: UUID="7ef07a2a-9ad0-464b-9244-6568278fd13d" TYPE="ext3" 
/dev/sda6: UUID="70ea9fef-f247-405e-8550-66db0a8fb5a2" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/robert/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=robert)


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7ef07a2a-9ad0-464b-9244-6568278fd13d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7ef07a2a-9ad0-464b-9244-6568278fd13d

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
uuid        7ef07a2a-9ad0-464b-9244-6568278fd13d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7ef07a2a-9ad0-464b-9244-6568278fd13d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        7ef07a2a-9ad0-464b-9244-6568278fd13d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7ef07a2a-9ad0-464b-9244-6568278fd13d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        7ef07a2a-9ad0-464b-9244-6568278fd13d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows 7 (loader)
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=7ef07a2a-9ad0-464b-9244-6568278fd13d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=70ea9fef-f247-405e-8550-66db0a8fb5a2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  86.4GB: boot/grub/menu.lst
  86.4GB: boot/grub/stage2
  86.2GB: boot/initrd.img-2.6.28-11-generic
  86.3GB: boot/vmlinuz-2.6.28-11-generic
  86.2GB: initrd.img
  86.3GB: vmlinuz
```

---

### Post by lindsay7 on 2009-05-21
Well there is something here that I just can not see. Just to make sure, when you installed grub did you do the following

in the terminal type.

"sudo grub"

at the grub prompt, type

"find /boot/grub/stage2

this will return something like (hd0,4)

still at the grub prompt type the results of what you get above
as such

"root (hdx,y)" where x and y are what you got in the above
"setup (hd0)"
"quit"

reboot


The Script Info looks like Windows should boot off of hd0,1.  As a last resort you should go into the grub menu and try hd0,0 just to rule it out.  If you still can not get this to work.  What I would do is start a new post with the info including the boot script info and explain you current situation and get some new eyes on this. There is something here that is missing and I can not see it.  Sorry I thought 
these steps would have done the trick.

---

### Post by tformed on 2009-05-21
When I did this before, I typed /boot/grub/stage1.

This time I did it with stage2 and got as follows:

btw what's the difference between stage1 and stage2? 

```
grub> find /boot/grub/stage2
 (hd0,4)

grub> root (hd0,4)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```

let me go ahead and try setting hd0,0 instead.

---

### Post by tformed on 2009-05-21
Same result, I'll go ahead and create a new thread for this then. I'm starting to wonder if maybe a BIOS setting is affecting this. Everything there is at default.

---

