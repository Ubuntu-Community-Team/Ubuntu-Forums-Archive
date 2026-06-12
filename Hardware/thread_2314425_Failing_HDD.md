---
title: "Failing HDD"
date: 2016-02-21
forum: Hardware
---

### Post by mayagrafix on 2016-02-21
I have a dual boot primary HDD that is about to fail. It has Win7 and Ubuntu. I made a Disk Image of the Windows partition and another for the Ubuntu partition using Gnome-Disks, and saved them to another HDD. My question is: When I install the new HDD I can just restore the aforementioned Disk Images to the new partitions and all will be OK? Including the Windows image?

[IMG][http://i.imgur.com/fcOpg63.png](http://i.imgur.com/fcOpg63.png)[/IMG]

---

### Post by sudodus on 2016-02-21
If you 'only' have images of the partitions, you must also

- install a grub ***bootloader*** and

- create a ***swap partition*** with the correct UUID or edit /etc/fstab to match the UUID of the new swap partition.

-o-

I use ***Clonezilla*** to make compressed images of the whole drive. It is straightforward to restore from such an image to a drive of the same size or larger, if it is an MSDOS partition table. If it is a GUID partition table, GPT, and the new drive is not exactly the same size, there might be problems. In that case you can try to fix it with ***gdisk*** (from the 'recovery & transformation' menu or the 'expert' menu).

---

