---
title: "Changed size of Ubuntu partition, now I get: &quot;missing operating system&quot;"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by Peasantoid on 2009-03-06
Hey everyone. My Google skills sorta suck, so sorry if this question has already been asked (don't worry, I will be very bashful).

I successfully installed Ubuntu on my second-generation MacBook, got it working properly, and installed all the latest updates. However, I realized my 8 GB of partition space would not be enough, so I installed GParted and resized things. Then I realized that in order to resize the Ubuntu partition, I'd have to use the live CD (8.04, 64-bit). Which I did.

/dev/sda1: FAT32: EFI partition...? (Didn't mess with this.)
/dev/sda2: HFS+: Mac OS X partition (Made this smaller.)
/dev/sda4: swap: Swap partition (Made this slightly larger.)
/dev/sda3: ext3: Ubuntu partition (Made this larger.)

When I tried to boot from the Ubuntu partition, I got the message "Missing operating system". I assume this is a problem with the bootloader (GRUB). I was fully able to mount and browse /dev/sda3 while running the live CD, so that seems to be all right. It just isn't bootable.

Any ideas as to how I can fix this? I would really like to keep my Ubuntu; I spent many sleepless nights configuring it.

[edit] Also, I didn't know which section would be best for this kind of thing, so yeah.

---

### Post by lindsay7 on 2009-03-06
Maybe this will help.

---

### Post by lindsay7 on 2009-03-06
Sorry too fast on the enter button.

[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

---

### Post by yther on 2009-03-06
I don't think you have a serious problem here.  What happened is probably that in resizing your partitions, you changed the starting point of the one where GRUB is installed, so when it's trying to start up, it gets lost.  The link given above should teach you a lot about how the whole GRUB thing works, and it does have a section on fixing things.  :)

You're lucky to have a modern Mac, BTW.  If you had an older (non-Intel) one you'd have to use a different boot loader that I found much less friendly than GRUB.

---

### Post by Peasantoid on 2009-03-06
Ah. I see the section "You resized a partition; GRUB is gone". So I need to do this from the live CD:
```
fsck.ext2 /dev/sda3 # fsck.ext3?
tune2fs -j /dev/sda3 # tune3fs?
mount -t ext3 /dev/sda3 /mnt/sysimage
cd /mnt/sysimage/bin
grub
```
I just need confirmation before I go ahead and break something even more important.

This "different boot loader" would be LILO? I tried installing a distro with that on an iBook G4 once. It failed and made me sad. :(

---

### Post by lindsay7 on 2009-03-06
See if this help,

From within Ubuntu, open a Terminal. then:

sudo gedit /boot/grub/menu.lst

This is the file containing the boot order. Any line begiining with a hash (#) is a comment.

Towards the bottom, you will see the Windows boot instructions. Cut and past so that those instructions precede the boot instructions for your ubuntu. I don't mean put them at the top of the file, I mean relative to the other boot instructions.

Just keep in mind that there are several "sample" boot instructions, commented out.

Save the file, then you can reboot.

What if you made a terrible mistake, and bungled the editing? All is not lost. You can edit that file using something such as a live Linux distribution on a USB stick. Just keep in mind that you need to edit the menu.lst file on your hard drive, not the one within the live Linux distro.

---

### Post by Peasantoid on 2009-03-06
Wait, let me get this straight. I need to edit the GRUB menu file, find the *Windows* boot instructions, and stick them before the others.

In the meantime, I'ma go get me some Super Grub Disk. [edit] ...which didn't even boot, so meh. Time to bite the bullet and edit some files.

---

### Post by Peasantoid on 2009-03-06
Huh. I really don't see why that would help my current situation. Also, I notice you posted those exact instructions in a thread about a different problem. Unless there's something I'm missing (more than likely), could I have something more specific?

I've looked at that article several times and haven't found anything about this particular issue. The "You resized a partition; GRUB is gone" section did nigh-on zilch. I'm kind of up a creek here.

Or, in more concise terms: HEEEELLLLLP MEEEEEE ;)

---

### Post by lindsay7 on 2009-03-06
I think I confusued you I just sent you this as an example for editing the grub file.  I was not suggesting that you needed to follow it. I should have made the clear. Sorry for the mess up.

---

### Post by Peasantoid on 2009-03-06
It's okay. I'm very easily confused.

But I still have no idea what to do...

---

### Post by lindsay7 on 2009-03-06
I am not sure how to fix you gurb file without messing it up by experimenting. I would run the edit command   sudo gedit /boot/grub/menu.lst
and see that the file says if you do have the file. Then I would start a new post with that in the body and an explanation of what you situation is. Hopefully, an expert to gurb files can make this easy.

---

### Post by Peasantoid on 2009-03-06
Awright then.

---

### Post by Peasantoid on 2009-03-07
The contents of */boot/grub/menu.lst* are as follows:
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
# kopt=root=UUID=71fc5242-cc44-42b4-8098-bee17299cb7c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=71fc5242-cc44-42b4-8098-bee17299cb7c ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=71fc5242-cc44-42b4-8098-bee17299cb7c ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=71fc5242-cc44-42b4-8098-bee17299cb7c ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=71fc5242-cc44-42b4-8098-bee17299cb7c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```
The root locations are fine. (hd0,2) == /dev/sda3 iirc, so no problem there. Basically, the bootloader config file is in working order.

 Like yther said, my problem is most likely due to GRUB's partition being in the wrong place. But how, in the name of all things (un?)holy, do I fix that?

---

### Post by Peasantoid on 2009-03-07
I'm writing this post in Ubuntu! \o/

Here's a quick rundown of what I did to fix the problem. First, I booted the live CD, then opened a Terminal window.
```
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sda3 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub
```
Now for the GRUB magic:
```
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,2)
grub> root (hd0,2)
root (hd0,2)
grub> setup (hd0,2)
[some output happened]
```
And then I rebooted and everything worked. Hallelujah!

Many thanks to everyone (including Tosk, who originally posted these wonderful instructions). You da man! Booyah! ... I'ma get some sleep now.

---

### Post by yther on 2009-03-07
> **Peasantoid said:**
> This "different boot loader" would be LILO? I tried installing a distro with that on an iBook G4 once. It failed and made me sad. :(

Nope, **yaboot**, a PowerPC-specific boot loader.  :)  I didn't like it as much because you couldn't just edit a text file from a liveCD to fix it, you had to reinstall it on the boot sector every time you made a change to the configuration.  Not really difficult (when it was working) but it did take me several tries to get it right the first time.

Looks like my guess was pretty close to your situation.  Once you reinstalled GRUB to your partition you're good to go, eh?  Cool!

I figured the partition's boot sector got lost when you resized it by moving its beginning.  Good thing someone had guides handy for the fixup.  [bookmarks guide for future use]

---

### Post by Peasantoid on 2009-03-07
Yup, this is why the Internet was invented.

Anyway, now that I've cleared this hurdle, I'm well on my way to making Ubuntu my primary OS. :)

---

