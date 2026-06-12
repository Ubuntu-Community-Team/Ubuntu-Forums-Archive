---
title: "unclean shutdown - manual fsck?"
date: 2008-12-14
forum: Hardware
---

### Post by raucous on 2008-12-14
So when I start my laptop up I am told that a fsck check will occur because of an unclean shutdown. It always stops at 69% and tells me I need to run the fsck manually which I have tried, but my novice ubuntu skills don't get me very far. It might be a physical problem. 

Anyway, these are my concerns:

I need to save my hard-drive with my photos and music and documents and all. 
-is there a way of accessing and backing up my Home Folder through the live cd? (Which I'm using as we speak - leading me to believe it isn't a physical problem)

Not a huge deal if I need to redo my settings and download my programs again - though I'd like to avoid that.

Or if someone could walk me through a manual fsck check I would be most thankful. 


Interestingly, I have been trying to get this thing going for about a week and 99% of the time I can't log on, but twice I was able to get to the log in screen and access my hard-drive, which quickly froze up on me.

At the end of the day all what I'm mostly concerned about is my documents because I haven't had the chance to back some of them up yet.

Is it possible to reinstall Intrepid without erasing the hard drive?


I feel how I did when I was 18 and the engine in my Dodge Charger seized while I pulled into Mr. Oil Change.


Thanks in advance.

---

### Post by taurus on 2008-12-14
You first need to mount your partition where /home is resided or / if you don't have a separate /home partition.  Then, you can access your personal files.  Assuming you only have / and it is /dev/sda1, open a terminal and run

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
ls -la /media/ubuntu/home
```
You can navigate to your $HOME with nautilus if you wish.  Remember, it is in /media/ubuntu/home/<your_username>.

---

### Post by raucous on 2008-12-14
Taurus, 
Thanks for the reply, I've seen your other posts and they've helped me in the past. 

How do I use nautilus?

(I only have on partition and currently I'm working off the live cd).

---

### Post by cariboo on 2008-12-14
If you are copying your files to an external drive you may need to run nautilus as root, to do this press Alt-F2 and type:

```
gksu nautilus
```

The will start nautilus in /root so you will have to navigate to where your home folder is mounted, then copy your files.

I would suggest once you have your problems repaired that you use sbackup to back up your files, it can be setup to backup files in the background and at scheduled times. 

Jim

---

### Post by raucous on 2008-12-14
great! got to my files but that still doesn't solve my fsck problem. Do you have any suggestions on that?

---

### Post by albinootje on 2008-12-14
> **raucous said:**
> So when I start my laptop up I am told that a fsck check will occur because of an unclean shutdown. It always stops at 69% and tells me I need to run the fsck manually which I have tried, but my novice ubuntu skills don't get me very far. It might be a physical problem. 
--- cut ---
Is it possible to reinstall Intrepid without erasing the hard drive?


To run fsck manually you need to know which partition you want to use fsck on.

For example : sudo fsck /dev/sda1
where /dev/sda1 would be the partition you want to run fsck on.

And about reinstalling Intrepid without erasing the hard disk :
During a normal Ubuntu installation you are forced to re-format your / partition. 
So if you have installed everything in / and you only have a swap-partition and no other Linux-partitions like /home
then you first need to backup your important data to some external media.

---

### Post by taurus on 2008-12-14
Remember to unmount the partition first before you fsck it.

```
sudo umount /dev/sda1
sudo fsck -y /dev/sda1
```
And if your harddrive is about to go, fsck will not do a whole of good.

---

### Post by raucous on 2008-12-14
I got this: 


ubuntu@ubuntu:~$ sudo fsck -y /dev/sda1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 37912812 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 37912813 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 37912814 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 37912815 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 37912816 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 37912817 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 37912818 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 37912819 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 37912820 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 37912821 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 37912822 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 37912823 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 37912824 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 37912825 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 215482/9584640 files (3.4% non-contiguous), 17281350/38321041 blocks
ubuntu@ubuntu:~$

---

### Post by albinootje on 2008-12-14
> **raucous said:**
> 
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 215482/9584640 files (3.4% non-contiguous), 17281350/38321041 blocks
ubuntu@ubuntu:~$

Looks good! :)
Are there any files in /lost+found/ ?

---

### Post by raucous on 2008-12-14
i dont know about lost and found, but im back on board and everything is intact. So all this has convinced me i need backup. 

enter... [http://store.iomega.com/section?SID=020702bd3aac853081d5345119f25336a45:4760&secid=40119]("http://store.iomega.com/section?SID=020702bd3aac853081d5345119f25336a45:4760&secid=40119")


any suggestions on how to get drivers?

---

### Post by albinootje on 2008-12-14
> **raucous said:**
> i dont know about lost and found, but im back on board and everything is intact. So all this has convinced me i need backup. 

enter... [http://store.iomega.com/section?SID=020702bd3aac853081d5345119f25336a45:4760&secid=40119]("http://store.iomega.com/section?SID=020702bd3aac853081d5345119f25336a45:4760&secid=40119")


any suggestions on how to get drivers?

I never needed a driver for my usb-disk or usb-sticks or dvd-writers etc.
But to be 100 % sure, check Linux hardware databases like this :

[http://hardware4linux.info/search/](http://hardware4linux.info/search/)

With this one you can search for "Working USB mass storages".

---

### Post by sportster3 on 2009-01-15
> **raucous said:**
> i dont know about lost and found, but im back on board and everything is intact. So all this has convinced me i need backup. 

enter... [http://store.iomega.com/section?SID=020702bd3aac853081d5345119f25336a45:4760&secid=40119]("http://store.iomega.com/section?SID=020702bd3aac853081d5345119f25336a45:4760&secid=40119")


any suggestions on how to get drivers?

For backups I would suggest installing BackupPC on a separate cheap pc running Ubuntu.  BackupPC will automatically backup your pc every night and has a web interface you can use to restore.  There's even a BackupPC package in Ubuntu.

---

