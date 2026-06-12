---
title: "Umask on Automounted VFAT USB HD"
date: 2005-09-30
forum: Hardware &amp; Laptops
---

### Post by damonkohler on 2005-09-30
So when I plug in my VFAT USB HD, it's automatically mounted for me under /media/usbdisk. That's great and all, but I can't find the settings for that in /etc/fstab? I'd like to change the umask so that other users can read and execute.

---

### Post by mlomker on 2005-09-30
You'll have to [create an entry]("http://ubuntuforums.org/showpost.php?p=355988&postcount=8") if you want something other than the defaults.  Ubuntu uses **pmount** to mount removable media without needing an fstab entry, but they get mounted so that only root has write & mounting permissions.

---

### Post by damonkohler on 2005-10-01
Awesome, thanks. Does this work with other umasks? i.e. 755?

---

### Post by mlomker on 2005-10-01
[QUOTE=damonkohler]Awesome, thanks. Does this work with other umasks? i.e. 755?[/QUOTE]

Yes.  It's an inverse mask, so a chmod of 755 would be 022 in fstab.

---

### Post by rodneyorpheus on 2005-10-04
Tried this, doesn't work for me. I've tried every combination of advice I can find here, but my USB and Firewire drives stubbornly remain only read/writable by the primary user.

This makes network use of removable drives impossible. It's a showstopper for me. Unless I can find some way of fixing it, it's moving to another distro, which I really don't want to do :confused:

---

### Post by mlomker on 2005-10-04
> Tried this, doesn't work for me. I've tried every combination of advice I can find here, but my USB and Firewire drives stubbornly remain only read/writable by the primary user.

I'm admin for quite a few boxes and those commands do work, unless the partition is corrupt. Have you tried running fsck on it?  Are you sure it's VFAT (NTFS is read-only in Ubuntu).

Post this while your drive is mounted.

```

cat /etc/fstab
sudo fdisk -l
mount

```

---

### Post by rodneyorpheus on 2005-10-04
I've tried it with several disks and it definitely doesn't work with any of them - they are all mounted as belonging to the primary user with no possibilty of changing any permessions, even with sudo. And the disks are all VFAT.

Just tried the same hardware using SuSE 9.3 and it works fine with that, so it seems to be some sort of problem with Breezy.

Rodney

---

### Post by mlomker on 2005-10-04
> it seems to be some sort of problem with Breezy.


Could be.  I won't install the betas on my production machine--I just run them in VMWare.

---

### Post by barba on 2005-10-23
"Me too" want all users to have access to a big usb-disk. 

Tried to fix this in fstab as said above. Nope, it won't fly. Now my USB-disk appears on sdb instead of sda - and the pmount / hal / whatever -combination happily automounts it at /media/usbdisk with 'wrong' permissions.

Where on earth are these umask set? There has to be a configuration file that says where the disk appears (/media/usbdisk ) and  with what permissions. I can't find it.

Suggestions?

EDIT: The main problem is (maybe) that the disk wont mount until somebody logs on via the GUI, personally I would prefer that any usb-disk connected at boot would mount immediately with the permissions I prefer...

---

### Post by mlomker on 2005-10-23
> Suggestions?


Yes, post your fstab and the output of mount and fdisk -l commands from my previous post.

---

### Post by barba on 2005-10-23
The entries in fstab is not the issue here. They're correct. The problem is that the external usbdisk may appear at different places in /dev after boot, see below:

# grep "SCSI device sd" /var/log/messages
Oct 21 14:42:47 localhost kernel: [4294686.759000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
Oct 21 21:39:26 localhost kernel: [4294685.054000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
Oct 22 15:53:20 localhost kernel: [4294686.652000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
Oct 22 21:32:47 localhost kernel: [4315077.823000] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
Oct 22 21:41:21 localhost kernel: [4315592.376000] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
Oct 22 23:06:15 localhost kernel: [4294686.895000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
Oct 22 23:22:38 localhost kernel: [4294688.467000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
Oct 23 00:58:33 localhost kernel: [4300470.029000] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
Oct 23 12:04:25 localhost kernel: [4294689.769000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
Oct 23 12:58:59 localhost kernel: [4294688.883000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
Oct 23 19:13:28 localhost kernel: [4294687.903000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)

Therefore I can't put /dev/sda1 in fstab with 'auto' -flag set (I want it mounted at boot) - if the device has changed place in /dev I'm in trouble.

IMHO the "right" way to handle external usb-disks would be that they automatically are mounted at boot in /media with the permissions (and owner if vfat) I choose. If I make static entries in fstab I pressume that the device always is present and always at the same place in /dev - this works for internal hd:s, but not with external.

---

### Post by mlomker on 2005-10-23
>  If I make static entries in fstab I pressume that the device always is present and always at the same place in /dev - this works for internal hd:s, but not with external.

They shouldn't change positions if you always have the same set of devices connected.  The permanent fix for this is to use UUID's in the fstab file rather than device names.  I don't have a couple USB devices that I can experiment with, otherwise I'd test it.

There's a [thread here.]("http://www.ubuntuforums.org/showthread.php?t=64674")  The posters had some issues with that approach under Hoary but I think it's worth pursuing.

---

