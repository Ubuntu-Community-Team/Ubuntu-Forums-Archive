---
title: "Automount Dingoo A320"
date: 2009-06-12
forum: Hardware
---

### Post by Harkins on 2009-06-12
I own a [Dingoo A320](http://en.wikipedia.org/wiki/Dingoo), which appears as a USB drive when connected to an XP/Vista/OS X computer but requires some manual setup in Ubuntu (Jaunty Jackalope, fully updated).

In Ubuntu, I connect it and see some new items in /dev/usb:

```

drwxr-xr-x  2 root   root         720 2009-06-12 10:49 block
brw-rw----  1 root   disk      8,  32 2009-06-12 10:49 sdc
brw-rw----  1 root   disk      8,  48 2009-06-12 10:49 sdd
drwxr-xr-x  2 root   root        4360 2009-06-12 10:49 char
crw-rw----  1 root   disk     21,   4 2009-06-12 10:49 sg4
crw-rw----  1 root   disk     21,   3 2009-06-12 10:49 sg3
crw-rw----  1 root   root    252,  34 2009-06-12 10:49 usbdev1.12_ep01
crw-rw----  1 root   root    252,  33 2009-06-12 10:49 usbdev1.12_ep81
crw-rw----  1 root   root    252,  35 2009-06-12 10:49 usbdev1.12_ep00

```

But the drive isn't automatically mounted like my USB drives and flash keys, which appear in the left column of the Nautilus file browser and output of 'mount' within a few seconds.

I can do:
```

$ sudo mount /dev/sdd /mnt
[sudo] password for harkins:
mount: /dev/sdd: unknown device
$ sudo mount /dev/sdc /mnt
mount: you must specify the filesystem type
$ sudo mount /dev/sdc /mnt -t vfat
$ ls /mnt
# ... all the files

```

After manually mounting it does not appear in the Nautilus Places but I can browse to it and read/write normally, and 'umount /mnt' to remove the drive.

I'd like it to be automatically mounted to a directory in /media like my other drives, and I'd like it to appear in the Nautilus Places menu. Automounting is pretty much magic to me, so this may be covered by TFM that I haven't found to RTFM. Any help would be appreciated.

---

### Post by Harkins on 2009-06-12
Well, I think I found TFM and it's not any help. I found [Mount/USB](https://help.ubuntu.com/community/Mount/USB) on the wiki and it only covers manually mounting. The [linked page](https://help.ubuntu.com/community/UsbDriveDoSomethingHowto) on doing things automatically has a big **THIS HOWTO DOES NOT WORK YET. The scripts are broken.** and I don't have the 'udevinfo' utility it mentions (and aptitude search doesn't turn it up either).

So no real luck there.

---

### Post by Mr.P1ckl3s on 2009-06-13
i was able to fix this by reformating the dingoo's internal storage in xp, if you have access to a windows box try backing it up, formating it and then see if it auto mounts in ubuntu.

anyhow when i couldn't for the life of me get it to mount fstab -l yielded this mess and i found the format in xp fix on a dingoo forum, can't remember link or i'd point you to it...

```
This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?      214466      419798   814758329+  74  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 36) logical=(214465, 70, 45)
Partition 1 has different physical/logical endings:
     phys=(366, 104, 37) logical=(419797, 101, 29)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?      167614      235530   269488144   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(107, 121, 32) logical=(167613, 119, 47)
Partition 2 has different physical/logical endings:
     phys=(10, 121, 13) logical=(235529, 37, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?       67918      244123   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(67917, 1, 18)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(244122, 1, 49)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?      492581      492589       32669+  bb  Boot Wizard hidden
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(65, 1, 0) logical=(492580, 59, 29)
Partition 4 has different physical/logical endings:
     phys=(96, 0, 7) logical=(492588, 89, 19)
Partition 4 does not end on cylinder boundary.
```

---

### Post by imaginarythomas on 2009-06-26
I too am having this problem but don't have an XP box at work. Have to use the wife's machine when I get home.

I did find the link Mr. Pickles was talking about for anyone else with this issue: [http://www.dingoo-digital.com/forums/i-need-help/cant-mount-dingo-64bit-win7-or-linux-distro](http://www.dingoo-digital.com/forums/i-need-help/cant-mount-dingo-64bit-win7-or-linux-distro)

What a wonderful little device! I can't wait to play some "Interesting Game"

---

### Post by ethoxyethaan on 2009-08-15
mount /dev/sdb /media/dingo -t vfat

only makes it writeable by root


edit fstab (/etc/fstab) and add:

/dev/sdb /media/dingoo vfat rw,user,noauto 0 0

then as normal desktop user run: mount /dev/sdb

now it should be writable by your user

---

### Post by manatlan on 2009-12-16
on karmic / 9.10
with dingoo (firmware 1.2)

I had formatted the internal ram as fat32 under a windows box.
now, when I plug the dingoo via the usb cable. Ubuntu mount it ...
But can't unmount it from nautilus ... taking a long time, and finish with a dbus error.

is there a trick to properly unmount the drive ?

---

### Post by newtonu on 2011-05-23
Hello all! I'm new to the forum, but a Ubuntu user for the last 3 years.

Anyone here had any luck finding an answer for this? Have my Dingoo here, but have not been able to mount it under Ubuntu. I'm using Ubuntu 11.04.

Thank you all.
[COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C]**[/COLOR][/FONT][/COLOR]

---

### Post by rby151 on 2011-12-07
I just got a Dingoo a320 and was horrified to find that my Ubuntu didn't automount it. I am SO glad for smart people who actually know things about computers--I just mounted it by saying some magic words to the terminal. I will get around to learning how all this stuff actually works...eventually....

---

