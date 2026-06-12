---
title: "GRUB won't recognize my windows install!"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by Andarion on 2009-02-23
Hey guys,

So, maybe you guys can help me. I installed Ubuntu on my machine today, and now I can't get into windows at all. I'm not given an option between the two operating systems.

I already had a very healthy version of Windows Vista Ultimate x64 running on my disk, taking up about 150GB of my 320GB HDD. 

This is how I installed ubuntu:

1) I put in the ubuntu 8.10 install disk and restarted my desktop.

2) I selected the correct language, region/time code, and keyboard settings.

3) I decided to manually partition my hard-drive. I did it as follows: Left my windows partition alone, created a 150gb partition for ubuntu in ect3 (i think), and a 2gb swap partition.

4) It installed, I entered my login info, it rebooted.

5) No windows.

This is the what GRUB spits out when I turn on my computer:

```

GRUB loading stage 1.5.

Grub loading, please wait.
press "esc" to to enter the menu...

Boot from (hd 0,5) ext3 (lots of numbers)

Starting up...
[0.04000] Aperture beyond 4GB. Ignoring.
Loading

```

I'm thinking about just putting in my windows disk and getting rid of Linux altogether, but I bet there's a way to get GRUB to recognize my window's install with the command prompt. Does anyone know the code?

BTW, here is my HDD according to GRUB.

```

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         15,120   625,136,399   625,121,280   f W95 Ext d (LBA)
/dev/sda5              15,183   307,208,159   307,192,977   7 HPFS/NTFS
/dev/sda6         332,171,343   625,136,399   292,965,057  83 Linux
/dev/sda7         307,208,223   311,109,119     3,900,897  82 Linux swap / Solaris

```

---

### Post by karthie on 2009-02-23
hi
did you tried the Easy BCD software 
google it is a free one get it and install in linux that one may help you to set up multi booting
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=1)
try this one may help you

---

### Post by Andarion on 2009-02-23
> **karthie said:**
> hi
did you tried the Easy BCD software 
google it is a free one get it and install in linux that one may help you to set up multi booting
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=1)
try this one may help you

First of all, I'm not sure what you mean by "install it in linux." I get an archive window, probably because linux can't by default install .exe's And I can't find a linux version anywhere.

Edit: So I figured out the whole WINE thing. Only, when I try to run EasyBCD I get a message that says:
```
~$ fixme:shell:DllCanUnloadNow stub
install the Windows version of Mono to run .NET executables.
```
Help?

Also, I went to that guide, and tried following it to get GRUB to recognize Windows. I followed the instructions to the T, and ran through the following problems.

First, when giving codes to grub to "setup hd(0)" it told me it could not mount that partition.

Secondly, when I hit Windows Vista, I get "error 12: Invalid device requested."

I'm all but done with this crap. This is getting really annoying! When I read up on this, it said that Ubuntu was supposed to automatically recognize windows!

Error 12: Invalid device requested

---

### Post by Mickser_52 on 2009-02-23
Hi,

 You could look at file /boot/grub/menu.lst. This lists out the options which grub gives ME at startup and check if windows is listed. 

On my laptop it shows the following at the end of the list.

.
.
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title		Other operating systems:
# root


title Microsoft Windows
root (hd0,0)
savedefault
makeactive
chainloader +1


If it is not there, you could add it on and see if it helps.

To look at the file open the terminal (Applications, accessories) and type sudo gedit /boot/grub/menu.lst then enter your password and gedit will open the file in a new window.

After an update I found that I had to edit this file as windows would not start. Also if i hibernate windows before I open ubuntu I get the cannot mount windows error message.

Hope this will help.

---

### Post by Mark Phelps on 2009-02-23
Don't know why you were told to use EasyBCD in Linux.  As best I know, it's strictly an MS Windows tool for managing the Vista Boot Loader.  I would be really surprised if it worked in Wine.

You could check out the NeoSmart forums site.  They provide EasyBCD and have some How-to's on its use.

---

### Post by caljohnsmith on 2009-02-23
The only NTFS partition you have is sda5, which is a logical partition. Windows will not normally boot directly from a logical partition unless you take special measures to configure it to do so. So if sda5 is your Windows partition, it looks like maybe it may have been converted from a primary into a logical partition somehow during the Ubuntu install process, because normally Windows is installed to a primary partition. In order to get a clearer picture of your setup related to booting Windows, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by directhex on 2009-02-23
Your partition ordering is broken, this is likely to be the cause of your errors. Windows is very fragile when it comes to partition tables. Notice that your sda7 is logically before your sda6 (looking at the partition start/end points)

I don't remember how to fix it, though

---

### Post by Andarion on 2009-02-23
> **caljohnsmith said:**
> The only NTFS partition you have is sda5, which is a logical partition. Windows will not normally boot directly from a logical partition unless you take special measures to configure it to do so. So if sda5 is your Windows partition, it looks like maybe it may have been converted from a primary into a logical partition somehow during the Ubuntu install process, because normally Windows is installed to a primary partition. In order to get a clearer picture of your setup related to booting Windows, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

Done.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa68e7d7b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         15,120   369,699,119   369,684,000   f W95 Ext d (LBA)
/dev/sda5              15,183   307,208,159   307,192,977   7 HPFS/NTFS
/dev/sda6         307,208,223   365,798,159    58,589,937  83 Linux
/dev/sda7         365,798,223   369,699,119     3,900,897  82 Linux swap / Solaris
/dev/sda2         524,800,000   625,139,711   100,339,712   7 HPFS/NTFS

/dev/sda2 ends after the last cylinder of /dev/sda

blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="E836A68236A6517C" LABEL="Backup" TYPE="ntfs" 
/dev/sda5: UUID="5C98FCB098FC8A32" TYPE="ntfs" 
/dev/sda6: UUID="f509ef06-0259-4d3f-b382-962c921e575d" TYPE="ext3" 
/dev/sda7: UUID="775fa5a0-8d99-4439-a6f3-3af5bf28d7d6" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)


=========================== sda6/boot/grub/menu.lst: ===========================

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
timeout		3

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
# kopt=root=UUID=f509ef06-0259-4d3f-b382-962c921e575d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f509ef06-0259-4d3f-b382-962c921e575d

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f509ef06-0259-4d3f-b382-962c921e575d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f509ef06-0259-4d3f-b382-962c921e575d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f509ef06-0259-4d3f-b382-962c921e575d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f509ef06-0259-4d3f-b382-962c921e575d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f509ef06-0259-4d3f-b382-962c921e575d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=f509ef06-0259-4d3f-b382-962c921e575d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=775fa5a0-8d99-4439-a6f3-3af5bf28d7d6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 158.1GB: boot/grub/menu.lst
 158.1GB: boot/grub/stage2
 158.1GB: boot/initrd.img-2.6.27-7-generic
 158.2GB: boot/vmlinuz-2.6.27-7-generic
 158.1GB: initrd.img
 158.2GB: vmlinuz
```

Thank you guys. I actually think the primary to logical switch might have been accidentally made by me when installing Vista. I'm not sure though, that's probably why Grub won't recognize my Windows install. 

I'm thinking about scrapping the current file-structure of my hard-drive, formatting everything and reinstalling windows with my Vista 64 recovery disk. But that'll prolly be a last-resort scenario, I really don't want to lose all my files.

@Mickser_52:

I already tried that, when I select windows it says "Error 12: Invalid Device Request."

---

### Post by caljohnsmith on 2009-02-23
It looks like your Vista install in sda5 is missing some of its boot files, and also its boot sector needs fixing in order to boot Vista from its logical partition. I would recommend following [meierfra's tutorial]("http://ubuntuforums.org/showpost.php?p=5726832") for how to restore your Vista boot files, and also to fix your Vista boot sector with "testdisk". As you will see from that tutorial, the Grub entry you should be using to boot Vista is:
```
title Windows Vista
rootnoverify (hd0,4)
chainloader +1

```
So as the tutorial emphasizes, do not include the "makeactive" line, because Grub can't set the boot flag on a logical partition (i.e. "make it active"). Anyway, let me know if you have any problems following that tutorial, or otherwise let me know how it goes.

---

### Post by Andarion on 2009-02-23
> **caljohnsmith said:**
> It looks like your Vista install in sda5 is missing some of its boot files, and also its boot sector needs fixing in order to boot Vista from its logical partition. I would recommend following [meierfra's tutorial]("http://ubuntuforums.org/showpost.php?p=5726832") for how to restore your Vista boot files, and also to fix your Vista boot sector with "testdisk". As you will see from that tutorial, the Grub entry you should be using to boot Vista is:
```
title Windows Vista
rootnoverify (hd0,4)
chainloader +1

```
So as the tutorial emphasizes, do not include the "makeactive" line, because Grub can't set the boot flag on a logical partition (i.e. "make it active"). Anyway, let me know if you have any problems following that tutorial, or otherwise let me know how it goes.

I followed that tutorial, and now I'm on a different boat stuck in the middle of the same ocean. When I try to boot to Windows from GRUB I get an Error 13: Invalid or Unsupported executable format.

I followed part 3 of that tutorial and this is what testdisk spit back at me when I tried to rebuild bs.

```
Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
     Partition                  Start        End    Size in sectors
 5 L HPFS - NTFS              0 241  1 19122 209 63  307192977

filesystem size           307192977
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               19199561
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.

```

What next?

BTW,thanks for all your help so far guys. Once I recover my files from old windows install I'm going to format my HDD, delete my partition table and start over again. I just need to get into the files, and ubuntu won't let me mount the windows drive.

This the error it spits back at me when I try to mount it:
```
**Cannot mount volume.**
Unable to mount the volume.
Failed to mount 'dev/sda5': input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FAkeRAIDhardware. In the first case run chkdsk /f on Windows than reboot into Windows TWICE. The usage of the /f parameter is very important! If you have SoftRAID/FakeRAID than you must activate it and mount a different device under the /dev/mappter/directory. (ege. /dev/mapper/nvidia_eahaacc1). Please see the 'dmraid' documentation for details.
```

---

### Post by caljohnsmith on 2009-02-23
What did you do between the time you ran the Boot Info Script in post #8 and your last post? The script was able to mount your sda5 partition just fine, yet you are showing in your last post that you couldn't mount sda5? What happened? How about posting the full output of:
```
sudo mount /dev/sda5 /mnt && ls -l /mnt
```

---

### Post by Andarion on 2009-02-23
> **caljohnsmith said:**
> What did you do between the time you ran the Boot Info Script in post #8 and your last post? The script was able to mount your sda5 partition just fine, yet you are showing in your last post that you couldn't mount sda5? What happened? How about posting the full output of:
```
sudo mount /dev/sda5 /mnt && ls -l /mnt
```

I didn't really do much...mounting that partition has always given me trouble in ubuntu.

```
Failed to mount '/dev/sda5': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
```

---

### Post by caljohnsmith on 2009-02-23
That's really strange then, because the script was able to mount your sda5 Windows partition. How about trying:
```
sudo mount -t ntfs /dev/sda5 /mnt -o force && ls -l /mnt
```

---

### Post by Andarion on 2009-02-23
> **caljohnsmith said:**
> That's really strange then, because the script was able to mount your sda5 Windows partition. How about trying:
```
sudo mount -t ntfs /dev/sda5 /mnt -o force && ls -l /mnt
```

Same error.

and I put the script through again and this is the result:

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
Failed to mount '/dev/sda5': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
Failed to mount '/dev/sda5': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa68e7d7b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         15,120   369,699,119   369,684,000   f W95 Ext d (LBA)
/dev/sda5              15,183   307,208,159   307,192,977   7 HPFS/NTFS
/dev/sda6         307,208,223   365,798,159    58,589,937  83 Linux
/dev/sda7         365,798,223   369,699,119     3,900,897  82 Linux swap / Solaris
/dev/sda2         524,800,000   625,139,711   100,339,712   7 HPFS/NTFS

/dev/sda2 ends after the last cylinder of /dev/sda

blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="E836A68236A6517C" LABEL="Backup" TYPE="ntfs" 
/dev/sda5: UUID="5C98FCB098FC8A32" TYPE="ntfs" 
/dev/sda6: UUID="f509ef06-0259-4d3f-b382-962c921e575d" TYPE="ext3" 
/dev/sda7: UUID="775fa5a0-8d99-4439-a6f3-3af5bf28d7d6" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=chris)
tmpfs on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=0755)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=f509ef06-0259-4d3f-b382-962c921e575d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f509ef06-0259-4d3f-b382-962c921e575d

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		f509ef06-0259-4d3f-b382-962c921e575d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f509ef06-0259-4d3f-b382-962c921e575d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		f509ef06-0259-4d3f-b382-962c921e575d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f509ef06-0259-4d3f-b382-962c921e575d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f509ef06-0259-4d3f-b382-962c921e575d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f509ef06-0259-4d3f-b382-962c921e575d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f509ef06-0259-4d3f-b382-962c921e575d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f509ef06-0259-4d3f-b382-962c921e575d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f509ef06-0259-4d3f-b382-962c921e575d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows
rootnoverify (hd0,5)
chainloader +1

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=f509ef06-0259-4d3f-b382-962c921e575d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=775fa5a0-8d99-4439-a6f3-3af5bf28d7d6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 158.1GB: boot/grub/menu.lst
 158.1GB: boot/grub/stage2
 158.2GB: boot/initrd.img-2.6.27-11-generic
 158.1GB: boot/initrd.img-2.6.27-7-generic
 158.1GB: boot/vmlinuz-2.6.27-11-generic
 158.2GB: boot/vmlinuz-2.6.27-7-generic
 158.2GB: initrd.img
 158.1GB: initrd.img.old
 158.1GB: vmlinuz
 158.2GB: vmlinuz.old
```

I have no idea what is going with my HDD, I think I might have screwed something up when I was using testdisk, because now I'm being offered two different ubuntu in the GRUB menu.

I'm going to install another version of Windows on my HDD and see if I can get to my old files that way. After that, I'm going to reformat my HDD.

---

### Post by caljohnsmith on 2009-02-23
It may be that you didn't recover the correct Windows partition with testdisk, i.e. the start/stop sectors could have been slightly off. How about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop (it's important to use the latest version), and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", "Y" to search for Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seem to be the partitions you want to recover.

---

### Post by Andarion on 2009-02-24
> **caljohnsmith said:**
> It may be that you didn't recover the correct Windows partition with testdisk, i.e. the start/stop sectors could have been slightly off. How about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop (it's important to use the latest version), and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", "Y" to search for Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seem to be the partitions you want to recover.

Ok, so first off, when I type "P" for the partition that I think is the one I want, I get a "Can't open filesystem. Filesystem seems damaged."

Also, during the process, it's telling me: "Warning: Incorrect number of heads/cyclinder 240 (NTFS) !=255"

Right now it's deep searching and at about 40%. We'll see what that brings up.

Edit: This is what it came up with.

```
Screen 1:

TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63

The harddisk (320 GB / 298 GiB) seems too small! (< 394 GB / 367 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                29775   0  1 48011  58 62  292965056
```

```
Screen 2

Warning: the current number of heads per cylinder is 255
but the correct value may be 240.
You can use the Geometry menu to change this value.
It's something to try if
- some partitions are not found by TestDisk
- or the partition table can not be written because partitions overlaps.

```

---

### Post by caljohnsmith on 2009-02-24
So what were the results of the deep search? Did it show a list of partitions it found? Also please post:
```
sudo hexdump -s24 -n2 -e '"%d\n"' /dev/sda5
sudo hexdump -s26 -n2 -e '"%d\n"' /dev/sda5
sudo xxd -s128 -l2 -p /dev/sda5
```

---

### Post by Andarion on 2009-02-24
> **caljohnsmith said:**
> So what were the results of the deep search? Did it show a list of partitions it found? Also please post:
```
sudo hexdump -s24 -n2 -e '"%d\n"' /dev/sda5
sudo hexdump -s26 -n2 -e '"%d\n"' /dev/sda5
sudo xxd -s128 -l2 -p /dev/sda5
```

Yeah, sorry about that. Here is is:

```

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 32667  54 27  524798721
D HPFS - NTFS              0 241  1 19122 209 63  307192977
D Linux                19122 211  1 22769 224 62   58589936
D Linux Swap           22769 226  1 23012 179 46    3900880
D HPFS - NTFS          32667  73 47 38913  37 36  100339712 [Backup]
D HPFS - NTFS          35087   6 56 35087 104 55       6174 [Boot]

```

This is what happens when I press P on those:
```

The first one states "Cannot list files, filesystem seems to be destroyed."

The second one contains the following:
dr-xr-xr-x     0     0         0 22-Feb-2009 12:28 .
dr-xr-xr-x     0     0         0 22-Feb-2009 12:28 ..
-r--r--r--     0     0         0 22-Feb-2009 19:44 CONFIG.SYS

The third one - Linux, contains this:

drwxr-xr-x     0     0      4096 23-Feb-2009 20:53 .
drwxr-xr-x     0     0      4096 23-Feb-2009 20:53 ..
drwx------     0     0     16384 23-Feb-2009 04:58 lost+found
drwxr-xr-x     0     0      4096 29-Oct-2008 17:28 var
drwxr-xr-x     0     0     12288 24-Feb-2009 09:40 etc
drwxr-xr-x     0     0      4096 23-Feb-2009 22:03 media
lrwxrwxrwx     0     0        11 23-Feb-2009 04:58 cdrom
drwxr-xr-x     0     0      4096 23-Feb-2009 20:47 bin
drwxr-xr-x     0     0      4096 23-Feb-2009 20:54 boot
drwxr-xr-x     0     0      4096 29-Oct-2008 17:18 dev
drwxr-xr-x     0     0      4096 23-Feb-2009 05:07 home
drwxr-xr-x     0     0     12288 23-Feb-2009 20:46 lib
lrwxrwxrwx     0     0         4 23-Feb-2009 04:58 lib64
drwxr-xr-x     0     0      4096 20-Oct-2008 08:27 mnt
drwxr-xr-x     0     0      4096 29-Oct-2008 17:04 opt
drwxr-xr-x     0     0      4096 20-Oct-2008 08:27 proc
drwxr-xr-x     0     0      4096 23-Feb-2009 17:22 root
drwxr-xr-x     0     0      4096 23-Feb-2009 20:48 sbin
drwxr-xr-x     0     0      4096 29-Oct-2008 17:04 srv
drwxr-xr-x     0     0      4096 14-Oct-2008 09:02 sys
drwxrwxrwt     0     0      4096 24-Feb-2009 07:35 tmp
drwxr-xr-x     0     0      4096 23-Feb-2009 18:53 usr
lrwxrwxrwx     0     0        30 23-Feb-2009 20:53 vmlinuz
lrwxrwxrwx     0     0        33 23-Feb-2009 20:53 initrd.img
lrwxrwxrwx     0     0        29 23-Feb-2009 05:09 vmlinuz.19250
drwxr-xr-x     0     0      4096 23-Feb-2009 18:53 lib32
lrwxrwxrwx     0     0        32 23-Feb-2009 05:09 initrd.img.old
lrwxrwxrwx     0     0        29 23-Feb-2009 05:09 vmlinuz.old

linux-swap contains nothing.

The fifth one contains this:
dr-xr-xr-x     0     0         0 26-Jul-2008 09:43 .
dr-xr-xr-x     0     0         0 26-Jul-2008 09:43 ..

And the sixth one contains this:
dr-xr-xr-x     0     0         0 15-Feb-2005 16:33 .
dr-xr-xr-x     0     0         0 15-Feb-2005 16:33 ..
dr-xr-xr-x     0     0         0 15-Feb-2005 16:33 System Volume Information

```

Also, here's what the command prompt spit out with those three lines you requested:
```

chris@daLINUXINATOR:~$ sudo hexdump -s26 -n2 -e '"%d\n"' /dev/sda5
255
chris@daLINUXINATOR:~$ sudo hexdump -s24 -n2 -e '"%d\n"' /dev/sda5
63
chris@daLINUXINATOR:~$ sudo xxd -s128 -l2 -p /dev/sda5
08cd

```

---

### Post by caljohnsmith on 2009-02-24
Based on the start/stop cylinders of the NTFS partitions that testdisk found, it looks like the second NTFS partition in the deep search results should be your Vista partition. The problem though is that partition is empty except for a single CONFIG.SYS file. I'm doubtful this will make any difference, but you might as well run a deep search with testdisk using the 240 heads, 63 sectors/track geometry that testdisk recommends, just to see if it makes any difference with the NTFS partitions it finds. So after starting testdisk again, choose "No Log", "Proceed", "Intel", but this time choose "Geometry"; then select "Heads", and change it to "240". After that, proceed with the steps from post #15 in order to do the deep search again. Let me know the results and we can work from there.

---

### Post by Andarion on 2009-02-24
Here is the new one.

```

Disk /dev/sda - 320 GB / 298 GiB - CHS 41346 240 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 34708 219 27  524798721
D HPFS - NTFS              1   1  1 20317 239 63  307192977
D Linux                20318   1  1 24192 239 62   58589936
D Linux                21969   1  1 41344 239 62  292965056
D Linux Swap           24193   1  1 24450 239 46    3900880
D HPFS - NTFS          34708 238 47 41345  52 36  100339712 [Backup]
D HPFS - NTFS          37279 231 56 37280  89 55       6174 [Boot]

```

I get the same result with reviewing the partitions with "p."

---

### Post by caljohnsmith on 2009-02-24
I think your current sda5 NTFS partition is most likely correct, so if you want to try and recover files from it, I would suggest first booting your Vista Recovery CD, go to the command line and do:
```
diskpart
```
And at the diskpart prompt do:
```
list volume
exit
```
Find the drive letter for the first NTFS partition on the drive (which should be your ~150 GB Vista partition), and then do:
```
chkdsk /r X:
```
Replace X with the drive letter of the Vista partition, and let me know if that command completes successfully or if it just returns an error. Also, in case your Vista Recovery CD is OEM, it probably wouldn't be a good idea to use it since it will most likely wipe the drive and reinstall Vista. Instead you can download a Vista Recovery CD from either of the following sources:

[http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/](http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/)
[http://www.pcworld.com/downloads/file/fid,71039/description.html](http://www.pcworld.com/downloads/file/fid,71039/description.html)

Good luck and let me know how that goes.

---

### Post by Andarion on 2009-02-24
Done.

This is what happened during the Chkdisk process.

Chkdsk verified files.
Chkdsk verified indexes.
Chkdsk deleted 13 index entries.
Chkdsk recovered lost files.
Chkdsk orphaned 13 files.
Chkdsk verified security descriptors.
Chkdsk verified Usn Journal
Chkdsk verified file data.
Chkdsk verified free space.

This is the end result:
```

Windows has made corrections to the file system.

153586499 KB total disk space.
 68965728 KB in 96155 files.
    60360 KB in 206977 indexes.
        0 KB in bad sectors.
   232248 KB in use by the system.
    65536 KB occupied by the log file.
 84339152 KB available on disk.

     4096 bytes in each allocation unit.
 38399122 total allocation units on disk.
 21084788 allocation units available on disk.
Failed to transfer logged messages to the event log with status 50.

```

(I might have gotten some of those numbers wrong, I had to type it up on my laptop.)

I'm thinking I might try that tutorial you posted earlier about reconstructing the boot info using the command prompt. When I tried that, I did it to the D: drive not the C: drive. Not sure why but I thought that was what windows was recognizing.

---

### Post by caljohnsmith on 2009-02-24
That's great, it looks like running chkdsk on your Vista partition completed OK. Have you tried mounting sda5 again in Ubuntu via the command in post #11 or post #13? Let me know what that returns.

---

### Post by Andarion on 2009-02-24
> **caljohnsmith said:**
> That's great, it looks like running chkdsk on your Vista partition completed OK. Have you tried mounting sda5 again in Ubuntu via the command in post #11 or post #13? Let me know what that returns.

First of all, I went back and completed part 2 of that original tutorial you gave me about rebuilding Windows' bootmgr files. Booting to Vista in GRUB still does not work, still and Error 13.

Secondly it did. And this is what it spit out in response to the code from post 13:

```
total 2096016
-rwxrwxrwx 1 root root          0 2009-02-22 17:44 AUTOEXEC.BAT
drwxrwxrwx 1 root root          0 2009-02-23 23:27 BOOT
-rwxrwxrwx 1 root root     333203 2008-03-29 13:01 bootmgr
drwxrwxrwx 1 root root       4096 2009-02-22 23:24 Config.Msi
-rwxrwxrwx 1 root root          0 2009-02-22 17:44 CONFIG.SYS
drwxrwxrwx 1 root root          0 2006-11-02 08:41 Documents and Settings
-rwxrwxrwx 1 root root 2145935360 2009-02-22 23:06 hiberfil.sys
-rwxrwxrwx 1 root root          0 2009-02-22 17:44 IO.SYS
-rwxrwxrwx 1 root root          0 2009-02-22 17:44 MSDOS.SYS
drwxrwxrwx 1 root root          0 2009-02-22 19:49 NVIDIA
drwxrwxrwx 1 root root          0 2008-01-20 20:03 PerfLogs
drwxrwxrwx 1 root root       4096 2009-02-22 23:13 ProgramData
drwxrwxrwx 1 root root       4096 2009-02-22 21:17 Program Files
drwxrwxrwx 1 root root       8192 2009-02-22 23:24 Program Files (x86)
drwxrwxrwx 1 root root          0 2009-02-22 19:38 $Recycle.Bin
drwxrwxrwx 1 root root       8192 2009-02-23 19:43 System Volume Information
drwxrwxrwx 1 root root       4096 2009-02-22 19:37 Users
drwxrwxrwx 1 root root      16384 2009-02-22 23:24 Windows

```

Should I go into testdisk and try to rebuild the bootsect?

---

### Post by caljohnsmith on 2009-02-24
Terrific, it looks like all or at least most of the Vista file system is there. Go ahead and do the testdisk procedure, and you will also need to do the "bootsect" command that the tutorial gives. Let me know how that goes or if you run into problems.

---

### Post by Andarion on 2009-02-24
> **caljohnsmith said:**
> Terrific, it looks like all or at least most of the Vista file system is there. Go ahead and do the testdisk procedure, and you will also need to do the "bootsect" command that the tutorial gives. Let me know how that goes or if you run into problems.

Yeah, ok. If I'm right, than according to testdisk, my Bootsect is fine, and I still can't boot into windows. Oh, and looking at my recovery disk, no bootsect.exe file exists in the boot directory.

```

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition                  Start        End    Size in sectors
 5 L HPFS - NTFS              0 241  1 19122 209 63  307192977

filesystem size           307192977
sectors_per_cluster	  8
mft_lcn                   786432
mftmirr_lcn               19199561
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.

```

...I'm seriously considering installing another version of windows, grabbing all my data and putting it on an external HDD, and then reformating my HDD.

---

### Post by caljohnsmith on 2009-02-24
OK, before you do a reinstall, how about trying this: download the attached "Vista_PBR_9sectors.txt" file to your desktop, and then do:
```
sudo dd if=~/Desktop/Vista_PBR_9sectors.txt of=/dev/sda5 bs=80 skip=1 seek=1 conv=notrunc
```
Then reboot, and let me know exactly what happens when you choose Vista from Grub.

---

### Post by Andarion on 2009-02-24
> **caljohnsmith said:**
> OK, before you do a reinstall, how about trying this: download the attached "Vista_PBR_9sectors.txt" file to your desktop, and then do:
```
sudo dd if=~/Desktop/Vista_PBR_9sectors.txt of=/dev/sda5 bs=80 skip=1 seek=1 conv=notrunc
```
Then reboot, and let me know exactly what happens when you choose Vista from Grub.

Done. Same Error. Error 13: Invalid or unsupported executable format.

---

### Post by caljohnsmith on 2009-02-24
From the script results in post #14, you are not using the Vista Grub entry that I recommended you to use; the entry should be:
```
title Microsoft Windows
rootnoverify [COLOR="Blue"](hd0,4)[/COLOR]
chainloader +1

```
In other words, (hd0,4) is sda5, not (hd0,5) like you had it. Let me know what happens when you use the above entry.

---

### Post by Andarion on 2009-02-24
> **caljohnsmith said:**
> From the script results in post #14, you are not using the Vista Grub entry that I recommended you to use; the entry should be:
```
title Microsoft Windows
rootnoverify [COLOR="Blue"](hd0,4)[/COLOR]
chainloader +1

```
In other words, (hd0,4) is sda5, not (hd0,5) like you had it. Let me know what happens when you use the above entry.

Wow. Ok, so it worked. Thanks a lot Caljohnsmith, I'm now looking at my vista screen. I have to decide now if I want to keep it this way until I get my new HDD in the mail, or reformat everything.

Either way, you've been a big help. It's kind of hilarious that I would'be been done awhile ago if I hadn't made that mistake. I guess I read the guide and not your code and assumed 5=5.

---

### Post by caljohnsmith on 2009-02-24
> **Andarion said:**
> Wow. Ok, so it worked. Thanks a lot Caljohnsmith, I'm now looking at my vista screen. I have to decide now if I want to keep it this way until I get my new HDD in the mail, or reformat everything.

Either way, you've been a big help. It's kind of hilarious that I would'be been done awhile ago if I hadn't made that mistake. I guess I read the guide and not your code and assumed 5=5.
Glad to hear that worked OK. Just as a side note, actually you wouldn't have been able to boot Vista sooner even if you had the correct Grub entry, because until we could make your Vista partition mountable and readable again using chkdsk, Vista would not have booted. The other issue was that your Vista partition boot sector was actually an XP boot sector, i.e. it would have tried to boot "ntldr" instead of Vista's "bootmgr". So even if you were using the correct Grub entry to start with, you would have gotten a "NTLDR missing" error when booting Vista. The "dd" command you ran from post #27 is what changed your Vista partition boot sector from an XP boot sector into a Vista one. Anyway, cheers and hope you don't run into any problems if you decide to reinstall.

---

