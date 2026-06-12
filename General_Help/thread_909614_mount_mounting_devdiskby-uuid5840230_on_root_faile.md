---
title: "mount: mounting /dev/disk/by-uuid/5840230 on /root failed: No such device"
date: 2008-09-03
forum: General Help
---

### Post by fibrinogen on 2008-09-03
Hi,

After Ubuntu installation by using Wubi Wubi-8.04.1-rev506 on my IBM R51 Notebook followed by an Update, the first reboot fails with showing the BusyBox screen and the following error message:

mount: mounting /dev/disk/by-uuid/5840230 on /root failed: No such device

What I already did:
[LIST]
[*]Did a chkdsk /r for the windows partition (NTFS)
[*]I used the Linux system-rescuce CD to mount the windows partition and the ubuntu root file to fix possible file system problems with fsck.
Used ntfx-3g to fix the NTFS partition flags and rebooted into windows to perform the chkdsk
[/LIST]

cat /proc/version signature
Ubuntu 2.6.27-2.3-generic

cat /proc/partitions
8  0  58605120 sda
8  1  53706208 sda1
8  2   4898880 sda2

mkdir /win
mount /dev/sda1 /win
mount: mounting /dev/sda1 on /win failed: Invalid argument

Can anyone help me?

Stefan

---

### Post by ago on 2008-09-04
I cannot see 5840230 in /proc/partitions. You might have run some software in windows that has changed the partition ID. If this is the case you will have to edit c:\ubuntu\wubi\disks\boot\grub\menu.lst accordingly and change the partition.

---

### Post by fibrinogen on 2008-09-04
Hi,

Thank you for your reply!

It was late last night. The full UUID is 584023054022E988 and this device is definitely existing in /dev/disk/by-uuid/.

I did not even boot into windows or run any other software between leaving the first Wubi Ubuntu session and reading this error message.

I thought the great number in /proc/partitions is the number of block used for this partition and has nothing to do with UUIDs?

What I did in detail from the beginning:
*Installed Ubuntu by using Wubi
*Installed other software inside the Ubuntu system (e.g. Firefox)
*Did an upgrade to the latest software Versions by using the Ubuntu function
*Did a system reboot which was not successfull. The system did not reboot and there were some error messages (I think network stuff) on the screen which I ignored.
*Did a hard reset
*Restarted the machine and received that mounting error message 
*Did that chkdsk /r
*Mounted the windows partition using ntfs-3g and mounted the loopback partition
*The error os still there

Any other idea?

Stefan

---

### Post by llh11456 on 2008-09-06
To everything [maple story items](http://www.maplestoryer.com/) there is a season and a time to every purpose under heaven.I hope you still take the time to run through the rain. no one can ever [maple story mesos](http://www.maplestoryer.com/) take away your precious memories. So, don't forget to make time and take the opportunities to make [maple story power leveling](http://www.maplestoryer.com/) memories every day!

---

