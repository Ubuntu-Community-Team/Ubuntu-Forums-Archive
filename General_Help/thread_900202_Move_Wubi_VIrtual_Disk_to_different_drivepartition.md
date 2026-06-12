---
title: "Move Wubi VIrtual Disk to different drive/partition?"
date: 2008-08-25
forum: General Help
---

### Post by rizky_p on 2008-08-25
I have a 7Gb(6g installed) of partition which being use by Ubuntu(Wubi), now i need a larger virtual disk for Ubuntu but the partition is full already. How can i move a Wubi Virtual drive into a different partition? i have a 20gig of free space to spare on a different partition. 

Thanks.
Rizki

---

### Post by rizky_p on 2008-08-28
anyone?

---

### Post by cormil on 2008-09-06
I have had the same problem and I did the following steps. I hope that these works also for you:

Boot in windows and move all the ubuntu directory (the name of the wubi directory is ubuntu for "ubuntu 8.04 hardy" and wubi for "ubuntu 7.10 festy") to the new disk/partition. 
Then edit the file D:\ubuntu\disks\boot\grub\menu.lst (change the disk letter to the letter of the destination disk/partition). Is necessary to change the *root* disk parameter and the *UUID* identifier to match the new disk/partition.
 
For example: 
 
I have moved the wubi installation from C: to D: and then I have changed the following lines: 
 
OLD VERSION
 
[I]root        (hd0,0)/ubuntu/disks
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=9A7006E17006C44B loop=/ubuntu/disks/root.disk ro quiet splash[/I]
 
 
NEW VERSION
 
[I]root        (hd1,0)/ubuntu/disks
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=763CE3323CE2EBD5 loop=/ubuntu/disks/root.disk ro quiet splash[/I]
 
To know the UUID of the different disk/partition is enough to boot the system from an Ubuntu LiveCD and use the vol_id /dev/<sda?>.

Let me know if these works also for you.
bye :)

---

### Post by IainPurdie on 2008-12-01
Rather than using UID=...., I think it's also possible to replace that with LABEL=.... where "...." is replaced by the drive label - a little easier to get at within Windows.

Alternatively, rather than using a LiveCD, create the new partition then use the existing installation to get the UID before you shift it and change the menu.lst file.

My main reason for moving mine is that I can't edit/delete files on the same partition as holds the WUBI install. I assume this is deliberate to stop the installation being corrupted, but is annoying when I just want to use the space! As the install doesn't increase in size, it made sense to create another partition just big enough to hold it, and move Ubuntu there instead.

Thanks to cormil for the hard work though :)

---

### Post by ago on 2008-12-02
That adds a new virtual disk:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

Otherwise modify menu.lst as described above, you can also use the /dev/sda1 notation (where a=hdd, 1=partition)

---

