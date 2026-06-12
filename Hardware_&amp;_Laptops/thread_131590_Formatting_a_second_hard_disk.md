---
title: "Formatting a second hard disk"
date: 2006-02-16
forum: Hardware &amp; Laptops
---

### Post by Connollyir on 2006-02-16
I need a non-GUI way to format a second hard disk for ubuntu storage. The reason I can't use a GUI is because the computer is headless and I administer it via ssh and the command line. Theres a 250GB disk with the operating system on it (sata) and another 80GB disk (primary Ide) and i need to format the 80 as supplementary storage to the 250.

Thanks

-Ian

---

### Post by taurus on 2006-02-16
If it's a second IDE drive, then

mke2fs -j /dev/hdb1

And if it's a SATA drive, then

mke2fs -j /dev/sdb1

If not sure, this command would help...

fdisk -l /dev/hdb
-or-
fdisk -l /dev/sda

---

### Post by Orpheus- on 2006-02-16
First, make a partition on the disk:

cfdisk /dev/hda

If your drive is not the primary IDE drive, it won't be hda, it'll be something else.

Note down the partition number (in your situation, the best thing to do is make one primary partition, which will be #1).

Make a filesystem on your new partition:

mkfs -t xfs /dev/hda1

If you want to use a different filesystem than xfs, put that in instead (other options are ext2, ext3, jfs, among others). hda1 refers to the disk (hda) and the partition number (1).

Now you have to mount it. To mount it temporarily, use:

mount /dev/hda1 /path/you/want/to/use

Add it to fstab if you want it mounted on boot.

---

### Post by Iowan on 2006-02-16
Are you at the **fdisk** (cfdisk) stage or the **mke2fs** stage?

The **man** page for **mke2fs** has details on ext3, too.

---

### Post by Connollyir on 2006-02-17
This is good. I really just needed a set of commands to start with since I was having issues remembering my stuff and I couldn't seem to find anything on it with a quick search (It was all GUI based).

Basically what I've got is a hard disk that used to be in a RAID 0 array and I threw it in this box for added storage. I think I'm going to stick with ext3 just for simplicity and speed.... come to think of it everything I run is in ext3.

It looks like I'm just going to make a single bootable partition (as suggested) and this should give me the extra living space I want. My question is though, how is this going to show up in the layout? As in I run this box as an FTP server for my personal computer and I'm curious as to how I am going to be able to access that disk through gftp? How am I going to see it once everything is up, running, and mounted - will it look like an extension of the /home directory from the 250 disk's OS or is it going to come up as a completely different directory (this seems much more likely now that I'm saying it) and if so how can I name it to what I want?

And Orpheus - why did you choose the xfs filesystem -  I'm unfamiliar with that flavor and would like to know more.

Thanks

-Ian

---

### Post by jamesr on 2006-02-17
Unless your /home directory is already too large, you could transfer the directory to the new drive and change the mount point so you just use /home on the new drive.

---

### Post by Orpheus- on 2006-02-17
[QUOTE=Connollyir]It looks like I'm just going to make a single bootable partition (as suggested) and this should give me the extra living space I want. My question is though, how is this going to show up in the layout? As in I run this box as an FTP server for my personal computer and I'm curious as to how I am going to be able to access that disk through gftp? How am I going to see it once everything is up, running, and mounted - will it look like an extension of the /home directory from the 250 disk's OS or is it going to come up as a completely different directory (this seems much more likely now that I'm saying it) and if so how can I name it to what I want?[/QUOTE]

That's entirely a function of where you mount it. If you mount it in /extrastorage it will show up there (this isn't recommended for various reason). One option might be to make it /home/yourusername/otherdisk if it's just you using the machine, or mount it as part of your ftp tree if you want to. It really does depend on the files you want to put on it. If you really want to get fancy you could look up LVM (but that's a bit of a chore to get working).

As for xfs... I don't like ext3. I think it's a bit of a hack on ext2, and xfs is a much better implementation of a journalling filesystem. Beware though, journalling filesystems are very much a religious thing. On a less civilised board, someone would flame me with "xfs? You're smoking something! ext3 is as good as it gets!" and then someone else would chime in with "No, if you don't use reiser you're a complete moron". Personally, and I do emphasise this is a personal opinion, I wouldn't touch anything other than xfs or jfs with a barge pole (except for /boot, which should be ext2 and small).

---

