---
title: "I don't know how to format my divices on Ubuntu..."
date: 2008-10-23
forum: General Help
---

### Post by ieBrazil on 2008-10-23
Help me! I would like to format my USB flashes using Ubuntu... I suppose it's possible, right?

How do I do?

Tnx.



ieBrazil

---

### Post by fjgaude on 2008-10-23
A normal way would be:

```
sudo mkfs -t -ext3 /dev/drive_name
```

You might have to look around to find the drive name. And you have choices for the file type you might wish to format. If you install **GParted**, its in the repository, it will show the USB device and its name, and from there you could format, install a filesystem.

---

### Post by C.S.Cameron on 2008-10-23
Using the Ubuntu Live CD go to Administration, System, Partition Editor.
Make sure you are seeing the correct drive using the button at the upper right, double check that the drive does not have more GIB than your flash drive. It is probably /dev/sdb if you only have one hard drive.
Right click on the partition and select "Unmount".
Right click on the partition and select "delete", click on the green check mark to proceed.
Right click on the empty space and select "Format to", select FAT32, click on the green check mark to proceed.
Close gparted and you should find that the drive is mounted and writable.
Good luck.

---

### Post by bodhi.zazen on 2008-10-23
You can install and use Gparted on your hard drive :

```
sudo apt-get install gparted
```

You can then use either the command line or gparted to format partitions.

mkfs.ext3 /dev/sdxy

see man mkfs

[http://linux.die.net/man/8/mkfs](http://linux.die.net/man/8/mkfs)

---

