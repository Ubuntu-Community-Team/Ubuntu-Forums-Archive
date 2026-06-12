---
title: "Can't mount NTFS drive from Live-CD"
date: 2008-09-05
forum: General Help
---

### Post by hrod beraht on 2008-09-05
I can't mount any NTFS drives from the Ubuntu Live-CD.

After booting the Live-CD, the hard-drive doesn't show up under Places --> Computer. But, if I do a *sudo fdisk -l*, I see it listed as /dev/hda1.

So, I did this:
[LIST]
[*]sudo mkdir /media/cdrive
[*]sudo mount /dev/hda1 /media/cdrive
[/LIST]
And the drive seemed to mount, but the folder has a big 'X' and it is completely inaccessible. Screenshot below:

[IMG]http://i48.photobucket.com/albums/f222/nutmeghill/Screenshot-media-FileBrowser.png[/IMG]

I tried on a different computer, which had an SATA drive partitioned into three parts:[LIST]
[*]/dev/sda1 Dell Utility
[*]/dev/sda2 HPFS/NTFS
[*]dev/sda3 CP/M / CTOS /...
[/LIST]
I mounted all three of those partitions in separate folders under /media and they all seemed to mount. But, sda1 and sda3 are the only ones I can access. The main NTFS partition is inaccessible and shows the folder with the 'X' as above.

Anyone know what I'm missing?

Bob

---

### Post by Elfy on 2008-09-05
Try this then - unmount it first

```
sudo umount /media/cdrive
sudo mount -t ntfs /dev/hda1 /media/cdrive
```

---

### Post by az on 2008-09-05
> **hrod beraht said:**
> I can't mount any NTFS drives from the Ubuntu Live-CD.

After booting the Live-CD, the hard-drive doesn't show up under Places --> Computer. But, if I do a *sudo fdisk -l*, I see it listed as /dev/hda1.

So, I did this:
[LIST]
[*]sudo mkdir /media/cdrive
[*]sudo mount /dev/hda1 /media/cdrive
[/LIST]
And the drive seemed to mount, but the folder has a big 'X' and it is completely inaccessible. Screenshot below:


I don't know why it is not automounting, but can you browse the contents by running

gksudo nautilus

once you mounted it as you describe?

---

### Post by hrod beraht on 2008-09-06
Specifying the type as **-t ntfs** didn't change anything (not shown on this screen). And **gksudo nautilus** definitely didn't work (as shown below).

[IMG]http://i48.photobucket.com/albums/f222/nutmeghill/Screenshot-ubuntuubuntu-2.png[/IMG]

---

