---
title: "[SOLVED] Upgrade problem 7.10 to 8.04"
date: 2008-09-27
forum: General Help
---

### Post by sqeelurgle on 2008-09-27
I just upgraded from 7.10 to 8.04.  When I rebooted there was an error message that said: "file not found   Error 17  Press any key to continue"

I pressed a key and got a text menu that let me select between 2 different kernels (low latency and standard) all with a 7.10 prefix, and "Ubuntu original kernel"  Every time I picked an option I got back to the original error message - except when I chose to boot to the original kernel.  When I did that it logged on fine, but I didn't have any mouse or sound.  The only thing I worked out how to do with no mouse was ctrl-alt-delete and shut down.

Can anyone give me some idea what to do next?

Thanks

---

### Post by raul_ on 2008-09-27
Post your /boot/grub/menu.lst please

You can open it from a Live CD or something

---

### Post by Sef on 2008-09-27
> Post your /boot/grub/menu.lst please

You can open it from a Live CD or something     That would not be correct for this problem.

This is GRUB error 17:

> Cannot mount selected partitionThis error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.       Open Konsole and type or paste this command:

```
sudo fdisk -l
``` Small L; then paste the results here.

Did you reformat the root parition as ext3 or kept it as ntfs?

---

### Post by raul_ on 2008-09-27
Humm you're right. I think I got that one and reinstalling Grub did the trick, but  that was a long time ago. I'll leave it for the pros :p

---

### Post by raul_ on 2008-09-27
[http://www.supergrubdisk.org/wiki/SuperGrubDiskProblems]("http://www.supergrubdisk.org/wiki/SuperGrubDiskProblems") (scroll down a bit)

Now I remember :)

---

### Post by sqeelurgle on 2008-09-28
My system is a wubi install on part of a windows partition.  From memory the virtual disks are all formatted as ext3

Just to cover everything - this is both of them:

fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e583e57

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76614d38

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24321   195358401    7  HPFS/NTFS


and this is /boot/grub/menu.lst

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'boot'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		1

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
# kopt=find=/wubi/boot/linux ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=find --set-root --ignore-floppies /wubi/boot/linux

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

## should update-grub add boot to the default options
## can be true or false
# boot=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-15-generic
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/wubi/wubi/wubi/boot/vmlinuz-2.6.22-15-generic find=/wubi/boot/linux ro quiet splash
initrd		/wubi/wubi/wubi/wubi/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/wubi/wubi/wubi/boot/vmlinuz-2.6.22-15-generic find=/wubi/boot/linux ro single
initrd		/wubi/wubi/wubi/wubi/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.20-16-lowlatency
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/wubi/wubi/wubi/boot/vmlinuz-2.6.20-16-lowlatency find=/wubi/boot/linux ro quiet splash
initrd		/wubi/wubi/wubi/wubi/boot/initrd.img-2.6.20-16-lowlatency

title		Ubuntu 7.10, kernel 2.6.20-16-lowlatency (recovery mode)
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/wubi/wubi/wubi/boot/vmlinuz-2.6.20-16-lowlatency find=/wubi/boot/linux ro single
initrd		/wubi/wubi/wubi/wubi/boot/initrd.img-2.6.20-16-lowlatency

title		Ubuntu 7.10, memtest86+
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntustudio-7.04-alternate-i386.iso quiet splash ro
initrd /wubi/boot/initrd
boot

---

### Post by Sef on 2008-09-28
> fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e583e57

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76614d38

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24321   195358401    7  HPFS/NTFS


GNU/Linux needs to be installed on ext3 (or another compatible file system.)  NTFS is not compatible with GNU/Linux.  Which drive did you install Kubuntu on?

---

### Post by blakamin on 2008-09-28
Edit:nevermind

---

### Post by sqeelurgle on 2008-09-28
> **blakamin said:**
> Edit:nevermind

What was here originally is correct - it's a wubi install - virtual disks

---

### Post by sqeelurgle on 2008-09-28
I have managed to copy down the error message from the bootup.  Here it is:

Booting 'Ubuntu 7.10, kernel 2.6.22-15-generic'
(hd 0,0)
Filesystem type is ntfs, partition type 0x7
kernel /wubi/wubi/wubi/wubi/wubi/boot/vmlinuz-2.6.22-15-generic find=/wubi/boot/linux ro quiet splash

Error 17: FIle not found.

I think there are a few puzzling things here:

I upgraded from 7.10 to 8.04 so why is it saying it is trying to boot 7.10?
The hard drive is ntfs, but ubuntu boots on a virtual drive thanks to wubi, and that virtual drive is formatted as ext3, so why is it saying the filesystem is ntfs?
This installation has been around a while.  It was first a 7.04 one, and was upgraded fairly recently to 7.10, which was also stable and worked well after the upgrade.  Now it is going to 8.04 (hopefully).  I would have thought that if the filesystem was going to be a problem then it would have been a problem a long time ago.

Looking at the grub menu.lst file above - this is the menu that appears once the "Press any Key" appears (after the error message given) and a key is pressed.  The "Ubuntu (origianl kernal)" part of that menu list is the only one that actually works and boots (although net access doesn't work but that is a problem for another time)

Any ideas?

Thanks

---

### Post by Sef on 2008-09-28
Moved to wubi forum.

---

### Post by sqeelurgle on 2008-09-29
bumpage

---

### Post by ago on 2008-09-29
> **sqeelurgle said:**
> 
title		Ubuntu 7.10, kernel 2.6.22-15-generic
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		**/wubi/wubi/wubi/wubi**/boot/vmlinuz-2.6.22-15-generic find=/wubi/boot/linux ro quiet splash
initrd		**/wubi/wubi/wubi/wubi**/boot/initrd.img-2.6.22-15-generic


well that is certainly wrong, replace with the correct path to the files, probably just /wubi/boot/vmlinuz... and /wubi/boot/initrd.img

---

### Post by sqeelurgle on 2008-09-29
> **ago said:**
> well that is certainly wrong, replace with the correct path to the files, probably just /wubi/boot/vmlinuz... and /wubi/boot/initrd.img

OK, this is one the way to the right solution.  I tried various things, and when I got down to just /boot/vmlinuz... then it booted properly the next time - and the menu.lst file had been altered to /wubi/boot/vmlinuz...

The next boot didn't work again, and it had been changed to /wubi/wubi/boot/vmlinuz...

It seems there is some process adding an extra /wubi in  either at every boot or every shutdown.

ANy ideas??

Thanks

---

### Post by sqeelurgle on 2008-09-30
I just did a text search, and the string "/wubi" occurs in the file "wubildr"  I could rename it or something and disable it, but that sounds like an important file.  Suggestions?

Thanks

---

### Post by ago on 2008-09-30
It's either a custom update-grub or a script in init.d.
I seem to remember it is the former, I think that a custom update-grub is installed and further updates are "blocked" in apt, you need to install the default update-grub. All that might have been done by lupin-support. Sorry, but 7.10 is not really supported (was never released beyond alpha) and I haven't got much time to fix that up.

---

### Post by sqeelurgle on 2008-09-30
Where do I get the default update-grub?  Is that just in the package manager somewhere?  

Thanks

---

### Post by sqeelurgle on 2008-10-01
Here is the header from my current update-grub.  I can post the whole thing if that would be useful, but it is a largish file:

#
# Insert a list of installed kernels in a grub config file
#   Copyright 2001 Wichert Akkerman <wichert@linux.com>
#   Copyright 2007, 2008 Canonical Ltd.
#
# This file is free software; you can redistribute it and/or modify it
# under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.
#
# Contributors:
#	Jason Thomas <jason@debian.org>
#	David B.Harris <dbarclay10@yahoo.ca>
#	Marc Haber <mh@zugschlus.de>
#	Crispin Flowerday <crispin@zeus.com>
#	Steve Langasek <steve.langasek@canonical.com>

---

### Post by sqeelurgle on 2008-10-02
bump

---

### Post by ago on 2008-10-03
sqeelurgle 8.10 is about to come out. It would be much simpler to install that afresh. You can back-up the old root.disk and then mount it in the new installation and copy over the files.

---

### Post by sqeelurgle on 2008-10-04
Sounds like a good approach.  Let me see if I understand the process fully.  I back up root.disk (within windows).  Then I do a new install of 8.10 to a new partition, then I copy root.disk back over the top?  If I do that will I keep all the installed packages I have installed so far?

Another though I have considered is transferring the whole lot to a permanent partition.  Is that likely to help solve the trouble or cause more?

Thanks

Hmmm, thinking more - the purpose of the backup is to make sure nothing gets badly stuffed up, and then wubi can re-install over the top of the original install without losing and data - in theory.  Is that correct?  It would make more sense that way.

---

### Post by sqeelurgle on 2008-10-05
One thing I have worked out.  Whatever process is adding the extra content to my menu.lst file must be operating on system shutdown.  Yesterday I bought a new monitor.  Due to some poor display resolution choices I had to perform a few hard resets (which thankfully didn't damage the system at all. So, there were about 8 or so times when the system booted up but was not properly shut down.  In that whole time the menu.lst file remained unchanged.  I assume therefore that it is system shutdown that is altering the file.  Is there any way for me to determine what is actually running at shutown?

Thanks

---

### Post by ago on 2008-10-06
No you install 8.10 then you mount the old root.disk. You do not copy it on top of the old one. Mounting means you access the content of the old installation, then copy selectively the files you need (usually under /home).

---

### Post by sqeelurgle on 2008-10-07
Ah, OK.  Can I copy over binaries for installed packages as well, and have them still work (I know you can't do that with Windows due to the registry, but I'm a relative newby to Linux)  I am on farly limited download allowances with my ISP and don't want to have to download all the software I have installed again if I can avoid it.

Thanks

---

### Post by ago on 2008-10-07
> **sqeelurgle said:**
> Ah, OK.  Can I copy over binaries for installed packages as well

No that is not possible. You can extract a list of the installed packages and "play it back" so that the same packages get reinstalled, but that will mean bandwidth...

---

### Post by sqeelurgle on 2008-11-03
This appears to have resolved itself.  A few days ago I installed a kernel upgrade, and ever since then the problem I was having appears to have resolved.  I assume part of the grub update process of updating the kernel has resolved the issue.

Thanks

---

