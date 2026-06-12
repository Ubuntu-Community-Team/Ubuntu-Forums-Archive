---
title: "Did FakeRaidHowTo and GRUB Hangs"
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by WalterDirt on 2006-02-09
I've been racking my brain trying to get my ICH5 RAID 0 setup using the following wiki:

[https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

Everything went smoothly for the most part. I think the menu.lst explaination was a bit vague. 

So after I'm done what happens is that my BIOS sits with 

GRUB

and that's all. It doesn't boot linux.

Here is my menu.lst file:
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
# root          (hd0,4)
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/mapper/isw_bicjjijhdb_SYSRAID7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,4)
kernel          vmlinuz-2.6.12-10-386 root=/dev/mapper/isw_bicjjijhdb_SYSRAID7 ro quiet splash
initrd          initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,4)
kernel          vmlinuz-2.6.12-10-386 root=/dev/mapper/isw_bicjjijhdb_SYSRAID7 ro single
initrd          initrd.img-2.6.12-10-386
boot

title           Ubuntu, memtest86+
root            (hd0,4)
kernel          memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


```


fdisk results:

```
Disk /dev/mapper/isw_bicjjijhdb_SYSRAID: 320.0 GB, 320083329024 bytes
255 heads, 63 sectors/track, 38914 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                             Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_bicjjijhdb_SYSRAID1               1       38914   312576673+   5  Extended
/dev/mapper/isw_bicjjijhdb_SYSRAID5               1           6       48132   83  Linux
/dev/mapper/isw_bicjjijhdb_SYSRAID6               7         388     3068383+  83  Linux
/dev/mapper/isw_bicjjijhdb_SYSRAID7             389       38914   309460063+  83  Linux
```
Can anyone help me with whats wrong?

---

### Post by WalterDirt on 2006-02-09
Anyone? Is there maybe an easier way to get software raid setup on Ubuntu? I'm losing my freakin mind trying to get this to work.

---

### Post by BenTyreman on 2006-02-09
Unless you want compatibility with Windows (i.e. you have a purely Linux system), then just delete the array in the RAID card BIOS and use fully-software RAID, available in the setup partitioning process.

Linux sees the RAID card as a SATA controller, not a RAID card. Thus, it detects two SATA hard drives. Keep a small partition at the front of each drive (around 50MB) for the boot partition on one and a dummy on the other. Use the rest as RAID. I prefer to have a dummy on the other to ensure the RAID partitions are as identical as possible, and don't miss out on 50MB.

This way, the kernel is stored on a simple partition, where it can bootstrap the RAID.

---

### Post by WalterDirt on 2006-02-09
Do you happen to have something I can follow to accomplish this? I'm new to this stuff. And I attempted to do it and GRUB install failed.

I setup the following:

SCSI1
50MB /boot
160.0 only for RAID

SCSI2
50MB /dummy
160.0 only for RAID

RAID0
320GB /

And it fails during the GRUB.

---

### Post by BenTyreman on 2006-02-10
What RAID card are you using? As far as I know, you will need to have the drivers for the card built into the kernel for it to be able to boot from the device.

---

### Post by WalterDirt on 2006-02-10
Ok well I tried what you said again and it seems to be working now. I think. 

I wasn't able to create a "swap" space for some reason. I was able to create /boot and /dummy and / but when i tried creating two partitions on the RAID portion one for root and the other for swap it wouldn't allow it

I'm not using a RAID card, I'm using the onboard ICH5 intel SATA controller.

Is there a way I can verify the speeds on the /boot and / drives to make sure the raid is working up to par? A utility or something?

Also, will not having a swap space cause me problems? I figure I have 3GB of RAM so I should be ok (at least in windows having that much ram and turning off swap isnt a big deal)?

---

### Post by BenTyreman on 2006-02-10
Perhaps I created two pairs of RAID areas (i.e. 2 per drive), one for swap and one for /. It's a while since I set it up. I definitely ended up with md0 being swap and md1 being /.

You should be pretty safe with 3GB of RAM for ordinary activities, although I always like a swap space, just in case.

AFAIK, the only way to speed test RAID arrays is to do something like
```
dd if=/dev/zero of=/tmp/dummy_file bs=10M count=100 oflag=sync
dd if=/tmp/dummy of=/dev/null bs=10M count=100 iflag=sync

```

---

### Post by psusi on 2006-02-10
[QUOTE=BenTyreman]
AFAIK, the only way to speed test RAID arrays is to do something like
```
dd if=/dev/zero of=/tmp/dummy_file bs=10M count=100 oflag=sync
dd if=/tmp/dummy of=/dev/null bs=10M count=100 iflag=sync

```[/QUOTE]

You don't want to do that because /tmp is mounted as a tmpfs, meaning it's all kept in ram.  Use the correct /dev node for the disk to do read/write testing on it.  Obviously don't write to it ( specify it to dd with of= ) if you have data on it.  

Walter, which partition is your /boot on?  Make sure by checking ls /boot/grub and if that looks ok, see which partition df says /boot is mounted on.  

When you issued grub the setup command, it did not complain I assume?  What filesystem did you format the partitions for?  ext3, or reiserfs?

Try adding the --force-lba option to grub's setup command.

---

