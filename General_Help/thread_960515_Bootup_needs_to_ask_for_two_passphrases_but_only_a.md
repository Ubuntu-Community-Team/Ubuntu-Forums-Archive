---
title: "Bootup needs to ask for two passphrases but only asks for one"
date: 2008-10-27
forum: General Help
---

### Post by Randomskk on 2008-10-27
Hi everyone,

I've just installed Kubuntu and used encrypted LVM. I have three hard drives and set them up as follows:
Drive 1 (/dev/sda)
  120GB NTFS (Windows XP)
Drive 2 (/dev/sdb)
  100MB ext3 /boot (/dev/sdb1)
  119.9GB   encrypted
Drive 3 (/dev/sdc)
  160GB    encrypted

The two encrypted volumes up make one volume group in LVM, called system. Inside system I then have my root, home, music and swap partitions.

At the moment grub loads fine and starts to boot, and then it asks for the passphrase for sdc1. I type this in and it hangs waiting for the root partition, which can not mount as sdb2 is still encrypted.
Eventually I am dropped to a busybox shell and can manually decrypt sdb2 using cryptsetup luksOpen /dev/sdb2 sdb2_crypt. Exiting the busybox shell causes the system to then mount root and everything proceeds as normal.

I'd like to have it ask for both passphrases at boot, so that both encrypted partitions are decrypted and boot can proceed without me needing to dig around in busybox. However, I can't find anywhere to specify what partitions should be decrypted for root.

/etc/crypttab is setup correctly as follows:
sdb2_crypt /dev/sdb2 none luks
sdc1_crypt /dev/sdc1 none luks

Originally UUIDs were used instead of device paths but I changed this for readability and so that the bootup screen asks for the passphrase to a device rather than a UUID - the erroe

When I'm in busybox I can go to /conf/conf.d/cryptroot and see two entries, one for system-root and one for system-swap, both with one UUID, and I presume those two entries are what's causing it to only try to decrypt that one partition. However I can't find this file and think it may be generated dynamically by /usr/share/initramfs-tools/hooks/cryptroot. That script seems to check /etc/fstab for the root partition's location and then I guess attempt to decrypt it. /etc/fstab is as follows:
> 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/system-root
UUID=5d81d21e-78bd-4a46-b8ac-2b2940ebd737 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=355886d8-1ab6-44b1-b662-7a99ace69854 /boot           ext3    relatime        0       2
# /dev/mapper/system-home
UUID=676ae1ce-f8cc-4029-8a03-4b4e75f8f115 /home           ext3    relatime        0       2
# /dev/mapper/system-music
UUID=eedd514e-ee47-4592-b44d-cd58e6005383 /media/music    ext3    relatime        0       2
# /dev/mapper/system-virtual
UUID=b8c5768a-40ad-4f7c-b520-3f7489b486dd /virtual        ext3    relatime        0       2
# /dev/mapper/system-swap
UUID=e3e239da-7ec8-4033-bb30-6f0dd157c245 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

There's only one UUID listed for the root partition which may be why it's not working, but I can't see that listing another there would help.

I have tried running update-initramfs to no success.

Does anyone have any suggestions on what I could do to get it to ask for both passphrases?

Thanks

---

