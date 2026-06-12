---
title: "BusyBox v1.1.3"
date: 2008-09-28
forum: General Help
---

### Post by bennoben on 2008-09-28
Hi i have been using ubuntu for about a month now and i really like it, but today when i powered up my computer i got a message saying

BusyBox v1.1.3 (debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built in commands.

i've tried rebooting and starting it up in recovery mode but its still the same message. im pretty new to ubuntu so i'd appreciate any help.
thanks

---

### Post by spiderbatdad on 2008-09-28
I have seen instances of busybox caused by improper shut down of windows in a dual boot scenario or by the improper removal of usb storage device. You might be able to fix by booting into windows and safely removing the usb hdd, or initiating a proper shut down.

---

### Post by bennoben on 2008-09-28
yeah well that's the problem i dont have a copy of windows on this computer, i built it myself and wanted the cheapest possible os which was linux and i never got round to installing windows on it

---

### Post by spiderbatdad on 2008-09-28
hmmm. well it might be tricky to pin down. Somehow the root file system has become unmountable. Perhaps the initramfs is locked up. The easiest first step might be to clear the cmos by powering down and using the onboard jumper and/or removing the battery for several minutes.

---

### Post by bennoben on 2008-09-28
well i cleared the cmos and it still has the same message

---

### Post by spiderbatdad on 2008-09-28
You can try to repair the problem from your live cd by booting it and mounting your installed file system:
```
sudo mount /dev/sdXY /mnt
```where "XY" is the partition...perhaps sda1.
It might help to know what changes you may have made to the system. Did it just spontaneously stop working?

Once the filesystem is mounted, perhaps try to repair menu.lst
```
sudo blkid
sudo cp /mnt/etc/fstab /mnt/etc/fstab.backup
gksudo gedit /mnt/etc/fstab &
```

Change the UUID in your fstab to match the UUID that blkid gives you. Make sure you change the UUID of the main Ubuntu partition mounted on root "/" and also the swap partition UUID. Next correct the UUIDs in your menu.lst:

```
gksudo gedit /mnt/boot/grub/menu.lst &
```

```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hdX,Y)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=77677cb5-6e56-4936-a373-80c15de06bca ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

Make sure you have the (hdX,Y) correct and also the UUID that corresponds to that partition.

Next you will most likely need to change the UUIDs in the following two files if you have them:
```


gksudo gedit /mnt/etc/initramfs-tools/conf.d/resume &
gksudo gedit /mnt/etc/uswsusp.conf & 
```

After you've got all the UUIDs corrected, do the following command to update your initramfs images:
```


sudo chroot /mnt
update-initramfs -u -k all
exit
```


Posted by caljohnsmith:[http://ge.ubuntuforums.com/showthread.php?p=5771495](http://ge.ubuntuforums.com/showthread.php?p=5771495)

---

### Post by bennoben on 2008-09-28
when i try to mount the hdd with ubuntu installed on it i get this message
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

does this mean that my hdd's been corrupted or something?:confused:

---

### Post by spiderbatdad on 2008-09-28
try to specify the fs type: sudo mount -t ext3 /dev/sda1 /mnt

---

### Post by bennoben on 2008-09-28
still comes up with the same message:(

---

