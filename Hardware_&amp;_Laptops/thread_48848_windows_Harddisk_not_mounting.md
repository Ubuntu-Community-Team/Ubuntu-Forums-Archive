---
title: "windows Harddisk not mounting"
date: 2005-07-14
forum: Hardware &amp; Laptops
---

### Post by pinak on 2005-07-14
I am quite new to ubuntu, i have used mandrake& redhat 9.
How do I mount my windows hard disk.
every time i boot the system i have to type in terminal mount /dev/hda1 /mnt/win_c.

is there an automated process where by the system automounts the hdd.

---

### Post by Umbra on 2005-07-14
Yes!!!

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by shrikantubuntu on 2005-07-14
/dev/hda1 is the location of your Windows partition (NTFS)
And Local mount folder : /mnt/win_c. 

You have to make an entry into _/etc/fstab_ file. The format is -

location_of_windows_partition [TAB] local_mount_folder [TAB] win_file_system [TAB] options [TAB] 0 [TAB] 0 

for example -

/dev/hda1       /mnt/win_c      ntfs      umask=0222      0       0

Now, I think you are clear with it.    ;-) 

shrikantubuntu

---

