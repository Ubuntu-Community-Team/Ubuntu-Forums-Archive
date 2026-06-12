---
title: "Worrying free space after formatting USB drive"
date: 2016-06-18
forum: Hardware
---

### Post by A Traveller on 2016-06-18
Hi all.

I have formatted two I TB USB drives (in Disk Utility) and upon opening them in the file manager, at the bottom of the window, they both show the amount of free space as 870.1 GB (the list in GParted shows 931.51 GB).

The info I seem to come across when researching this on the web is that ext4, which is what I have formatted both disks to, reserves some space for some reason or the other, but according to info on the web, this is just supposed to be 5%. There is also a file called 'Lost+Found' showing up on each drive.

I have searched for info on if it is safe to delete the 'Lost+Found' file, but it seems that this is not recommended.

My questions are:-

1) If ext4 reserves 5% of space, where has the rest of the space disappeared to (870.1 GB is nowhere near 5%!)?

2) If I only want to use the disks for files and not for an operating system, does ext4 still need to reserve its 5% space?

3) Similarly, if I only want to use the disks for files and not for an operating system, is the 'Lost+Found' file still not safe to delete?

4) Will I not be able to save any more files to the disk once I have used up 870.1 GB, or does the 'reserved space' automatically gives itself up? If so, how much space does it give up?

5) An unrelated question, but during the steps of formatting in Disk Utility, when you overwrite the name 'New Volume' with whatever name you choose (the first time during the process when Disk Utility lets you type a name), where does this name appear afterwards? The disks appear in the 'Places' menu with the name which you typed the second time Disk Utility lets you type a name, however, where does the first 'name' go?

It would be appreciated if anyone could shed any light on this.

Thanks.

---

### Post by weatherman2 on 2016-06-18
1Kilobyte = 1024 bytes

[http://www.howtogeek.com/123268/windows-hard-drive-wrong-capacity/](http://www.howtogeek.com/123268/windows-hard-drive-wrong-capacity/)

Lop off another 5% and your quoted sizes sound about right.  You can reduce that 5% to 0% if you want, with this command (make sure partitions not mounted first).  Open a terminal (Ctrl Alt t) and type:

```
sudo tune2fs -m 0 /dev/sdb1
```

(replace /dev/sdb1" with the real device ID for your partition.)

---

### Post by A Traveller on 2016-06-21
Thanks weatherman2.

---

