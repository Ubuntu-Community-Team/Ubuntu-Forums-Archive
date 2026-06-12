---
title: "&quot;Error 15: File not found&quot; with 9.04 to .10 upgrade"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by blackbird3216 on 2009-10-30
I just "finished" upgrading ten minutes ago, and now, it shows error 15. I don't understand what the issue is. I am assuming that it is keeping GRUB1. I opted to remove the old linux kernels during cleanup, and I don't know if that is a problem. I have a couple of different partitions, if I remember correctly:
boot: ext2
Home: ext3
/:ext4
swap: Swap

How can I fix this?

---

### Post by blackbird3216 on 2009-10-31
I tried running:
Find /grub/stage1
  (hd0,0)
root (hd0,0)
Setup (hd0)
Quit
Reboot

Error 15:File not found

I'm not sure if my abnormal partitioning has caused any issues with trying to reinstall grub. Is it actually installing the mbr in /(ext4) instead of boot (ext2), which would probably ruin things? How do I make boot(ext2) where its trying to find stage1? For some reason, I think the 9.10 upgrader installed the mbr in root, which does not have any of the booting files.

When i try "sudo gedit /boot/grub/menu.lst", the file is empty. Does this confirm my hypothesis?

---

### Post by blackbird3216 on 2009-10-31
> **blackbird3216 said:**
> I tried running:
Find /grub/stage1
  (hd0,0)
root (hd0,0)
Setup (hd0)
Quit
Reboot

Error 15:File not found

I'm not sure if my abnormal partitioning has caused any issues with trying to reinstall grub. Is it actually installing the mbr in /(ext4) instead of boot (ext2), which would probably ruin things? How do I make boot(ext2) where its trying to find stage1? For some reason, I think the 9.10 upgrader installed the mbr in root, which does not have any of the booting files.

When i try "sudo gedit /boot/grub/menu.lst", the file is empty. Does this confirm my hypothesis?
Can someone please help me? I've searched hours with no stable solution. Can I at least retrieve my files(last time I tried, it was encrypted)

---

### Post by blackbird3216 on 2009-10-31
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
# kopt=root=UUID=1ded233f-c141-4768-a8a9-fd13c60ff7e0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dfbd59e5-e0e8-4966-92f6-bc6f5e09cf43

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		dfbd59e5-e0e8-4966-92f6-bc6f5e09cf43
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=1ded233f-c141-4768-a8a9-fd13c60ff7e0 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		dfbd59e5-e0e8-4966-92f6-bc6f5e09cf43
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=1ded233f-c141-4768-a8a9-fd13c60ff7e0 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		dfbd59e5-e0e8-4966-92f6-bc6f5e09cf43
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=1ded233f-c141-4768-a8a9-fd13c60ff7e0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		dfbd59e5-e0e8-4966-92f6-bc6f5e09cf43
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=1ded233f-c141-4768-a8a9-fd13c60ff7e0 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
uuid		dfbd59e5-e0e8-4966-92f6-bc6f5e09cf43
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Ok, this is my menu.lst. are there any issues?

When I try to run sudo update-grub, I get
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

Is it becasue its trying to find grub in the root partition, but it is installed in /boot?

---

### Post by blackbird3216 on 2009-10-31
bump

---

### Post by michcaptk on 2009-10-31
blackbird,

I don't have an answer to your problem, but I wanted to let  you know I'm in the same boat.  I'll share any information if I figure it out.

---

### Post by zim2dive on 2009-11-01
Add 1 victim more to this unhappy party

EDIT: this is a single boot (Ubuntu only 9.04 currently) system.

---

### Post by robbiechad on 2009-11-01
I have similar problem . I am or was running a dual boot machine with Windows Vista Premium and Ubuntu 9.04 , both working perfectly, with Ubuntu my main system,  playing DVDs etc, I only used Vista for some apps that wouldnt run properly on Linux (my scanner) instead of leaving well enough alone I decided to upgrade to 9.10 (big mistake!!) I cannot boot my windows system as it has disappeared from the boot order, I get Error 15 when I try to boot other Operating Systems.   How can I get my original Linux & Windows Boot order Back?   Oh as well I have also lost my touch pad curser control as well.  (if your planning on upgrading to 9.10 a word of advice DON'T DO IT)

---

### Post by zim2dive on 2009-11-01
So.. 1 hour and lots of searching later..

I booted with an 8.04LTS USB disk.. I used > sudo fdisk -l to confirm my boot partition (/dev/sda1 in my case) and used> ls -l /dev/disk/by-uuid  to get my UUIDs.

I followed post #1 [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) to reinstall grub (I guess I can't say I'm sure WHERE that installed happened tho)

Then rebooted from the broken system... I waited for the Error 15, then hit "e" to edit and typed in my UUID... hit return..then hit "b" to boot.

After this I got to the Ubuntu graphic (with the horizontal bar) but then it failed and dropped into BusyBox...

When I rebooted the old UUID was back in the boot info... I don't see an option to save it?

So then I tried to "e" edit and hit return on each option.. they all fail with Error 15 (and annoying the old/wrong UUID keeps coming back)...

so then I edit the recovery mode entry and hit b from there.. again I get to BusyBox (which does not seem to be able to see /boot so I can't edit with that) ?  Not sure getting to BB does me any good.

EDIT2: I booted from a USB 8.04 stick.. looked at setting partitions manually and chickened out... it booted to 8.04 and then I used the places menu to mount my original HD.. I then typed> sudo gedit /boot/grub/menu.lst and editted out the offending UUIDs.  Saved and rebooted.. back to 9.04 working.

---

### Post by chaitanyagupta on 2009-11-02
Hello,

I faced the same problem, and thankfully I have been able to solve it now :) The issue was because of my partitioning scheme and grub entries in menu.lst. Basically, on my system,

/dev/sda1 is mounted on /boot
/dev/sda3 is mounted on /

After upgrading to Karmic, I got the dreaded "Error 15: File not found" message.

The solution for me was to boot into the live CD, mount my boot partition (/dev/sda1), open {boot partition}/grub/menu.lst, and modify the following:

kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=afe23e5b-9bb1-4dd8-8f23-acddc670711c ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

to this:

kernel		/vmlinuz-2.6.31-14-generic root=UUID=afe23e5b-9bb1-4dd8-8f23-acddc670711c ro quiet splash 
initrd		/initrd.img-2.6.31-14-generic

Hope this helps someone.

*Note:* Untested, but instead of doing the above and modifying menu.lst, if you create a (boot-->../) symlink in your boot partition, that should also work I think.

---

### Post by michcaptk on 2009-11-03
Thank you, chaitanyagupta.  That got me pretty close, but not all the way.  Once I followed your steps, I was getting an error that the UUID of my /boot partition could not be resolved.  I could see this error by using fsck from the command line.  I created my own UUID with uuidgen and put the new id in the /etc/fstab file, but that didn't seem to help... still get the same error.  My /boot partition (for me /dev/sdb1) seemed fine when I mounted it.  So then I copied all of my files in my boot partition to a temp directory.  I then used fdisk and mkfs to wipe out that partition.  I checked it with fsck, and it seemed ok.  So I copied the files from the temp back to my /boot drive (still containing chaitanyagupta's changes), and it worked.

For me, it seems as if my /boot partition got messed up somehow.

Since I'm going off of memory now (tried a lot of other things that did not work), this might be a little off.  But basically here are the commands:
Use a live CD to make the changes that chaitanyagupta described.
If that doesn't work and you get some error about UUID not being resolved, go back to the live CD and open a terminal.
Make sure you are root.
Mount your /boot drive with write permissions:  mount -t ext2 -o rw /dev/sdb1 /mnt/sdb1
(note you may need to adjust ext2 depending on your filetype.  Also your device may be something other than sdb1, so adjust accordingly... you may need to check your /etc/fstab)
Make a temp dir somewhere (not inside your /boot device)
Copy your files to the temp dir: cp -R /mnt/sdb1/* /tmp/backup-boot
Unmount your /boot device: umount /mnt/sdb1
Reset the partition:
fdisk /dev/sdb
---  p      (to print your partitions... look for your boot device, mine was "1";  remember your start and end cylinders;  also remember your blocks)
--- d       (choose the number of your boot device from prev step)
--- n      (choose same number of boot device and use same start/end cylinders)
--- a    (choose the same number of boot device; makes it a boot partition)
--- w    (this will save your changes)
Now format the partition:
mkfs -t ext2 /dev/sda <number_of_blocks_from_before>
Now verify format worked: fsck /dev/sdb1

Hopefully that all worked.  If so, remount the /boot drive and copy all of your files from the temp directory back into the /boot drive (same as when you copied them out but swap the two paths).

Now reboot (without the liveCD).

When I did this it got my system back up.  I hope this helps if you are getting the UUID issue too.

---

### Post by chaitanyagupta on 2009-11-03
I had encountered UUID issue too, but I wasn't sure if it was related, so I didn't write anything about it. Here's what I did to fix the UUID issue.

Open /etc/fstab, and look for an entry like this for your boot partition:

```

# /dev/sda1
UUID=xxx-xxx-xxx				  /boot           ext2    relatime        0       2
```

Now, remove the UUID=... field and replace it with the commented out /dev/sda1 column:

```

/dev/sda1				  /boot           ext2    relatime        0       2
```

I was able to reboot fine after this.

---

### Post by lindsay7 on 2009-11-03
From,   [https://wiki.ubuntu.com/Grub2#Error%2015%20-%20File%20not%20found](https://wiki.ubuntu.com/Grub2#Error%2015%20-%20File%20not%20found)


Error 15 - File not found

This error means that while grub2 is installed to /boot your Master Boot Record ( mbr ) still contains grub legacy. This can happen if you don't select your drive when running "sudo update-from-grub-legacy".

    *

      First, grab a copy of the latest Ubuntu LiveCD and boot it.
    *

      Open a terminal and type

      $ sudo fdisk -l

    *

      Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt

      $ sudo mount /dev/sda1 /mnt

    *

      If you have /boot on a separate partition, that need's to be mounted aswell. For reference, /dev/sda2 will be used.

      $ sudo mount /dev/sda2 /mnt/boot

      Make sure you don't mix these up, pay attention to the output of FDISK
    *

      Now mount the rest of your devices

      $ sudo mount --bind /dev /mnt/dev

    *

      Now chroot into your system

      $ sudo chroot /mnt

      You should be chroot'd into your system as root, you can now run commands as root, without the need for sudo.
    *

      Tell grub what drive it should install itself to (press space bar to select a drive and don't continue without selecting one)

      $ dpkg-reconfigure grub-pc

    * Press Ctrl+D to exit out of the chroot.
    *

      Once you exit back to your regular console, undo all the mounting, first the /dev

      $ sudo umount /mnt/dev

    *

      Now you can unmount the root system

      $ sudo umount /mnt

      And you should be free to restart your system right into GRUB 2 and then into your system installation.

---

