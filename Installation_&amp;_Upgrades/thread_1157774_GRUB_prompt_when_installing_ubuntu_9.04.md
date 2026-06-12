---
title: "GRUB prompt when installing ubuntu 9.04"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by drifter129 on 2009-05-13
Hi guys - i was trying to install linux on my system to dual boot with windows vista, but had problems. when i tried booting in linux i just got a message saying "no boot device. insert system disk".
I then tried installing linux using the "use entire disc" option, thus overwriting the existing windows install completely. This appeared to go through ok, but when trying to boot up ubuntu, i just get a prompt which says 'grub> ' and don't know what to do.
I have done a search in google but wasn't able to find anything helpful.

---

### Post by Lampi on 2009-05-13
You should boot your live cd of jaunty again, open a terminal, run 'sudo su', mount the partition you installed jaunty into and then type:

```
grub-install --recheck --no-floppy --root-directory=/path/to/your/jaunty/mount/point /dev/sd<LETTER>
```

where LETTER is the disc your jaunty partition is on (if it's on sda1 the letter is "a", so use **sda**)

This will recreate Grub in your Master Boot Record and recreate the entries in your /boot directory

---

### Post by drifter129 on 2009-05-13
grub > root
 (hd0,0): filesystem type is ext2fs partition type 0x83

grub > root (hd0,<tab>
 partition num 0, filesystem type is ext2fs, partition type 0x83
 partition num 4, filesystem type is unknown, partition type 0x82

---

### Post by drifter129 on 2009-05-13
thanks lampi will give that a try now

---

### Post by drifter129 on 2009-05-13
sorry to be a noob, but to mount the partition, do i type?
mount /dev/sdb1  ?
tried this and didn't work, but in know the drive is definately sdb..

---

### Post by Lampi on 2009-05-13
you can check this by double clicking the disk icon in nautilus. This should mount your drive to /media/<LABEL>

where LABEL is the name you gave your root partition when you installed your Ubuntu from CD

If you didn't assign a name you will find it in /media anyway - it just will show up as block device e.g /media/sda1 if it is sda1

you can check your mount point using:

mount -l

or

cat /proc/mounts

---

### Post by mountaintop on 2009-05-13
When you get grub> message try to press Esc button.

---

### Post by drifter129 on 2009-05-13
sorted!!! 
thanks for your help lampi

---

