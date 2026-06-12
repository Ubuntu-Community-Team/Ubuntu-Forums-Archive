---
title: "Problem with imaged partition of ubuntu"
date: 2008-09-30
forum: General Help
---

### Post by sh4dow_cr4ft on 2008-09-30
Hi, 

I currently have a laptop with a dual boot of xp/ubuntu, and the hard drive in the laptop was failing. 

So I made an image with Norton Ghost version 8, received a replacement hard drive and imaged it with the image I recovered with Norton ghost.

However, now when I try to boot into ubuntu, I get the error :

"/dev/sda5: Resize inode not valid.

/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(e.e, without -a or -p options)
fsck died with exit status 4

*An Automatic file system check (fsck) of the root filesystem failed. [fail]
A Manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.

*The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started. After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system. Give root password for maintenance
(or type Control-D to continue)

------------------------------

I give the root password

and get: 

------------------------------

bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found

-------------------------------

So I type:

fsck /dev/sda5 

and get:

-------------------------------

fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
Resize inode not valid. Recreate<y>?

--------------------------------

I choose yes 
and get:
---------------------------------

Backing up journal inode block information.

/dev/sda5 contains a file system with errors, check forced.

Pass 1: Checking inodes, blocks, and sizes
Group 0's inode table at 8 conflicts with some other fs block.
Relocate<y>?

--------------------------------

I choose yes
and get the same thing but the 8 counts up to 9 and on and on it goes, until it stops for a moment writes to the hard disk, and starts again from the beginning.

-

The hard drive was replaced as it had bad sectors, but the xp partition seems to work fine.

I should also add, after the image was done, I had to correct Grub on the partition as the Ghost version 8 ignores that part of the MBR for an image.

Grub now works fine displaying all boot options, and boots into windows fine.


Thanks for your help

---

### Post by Sycron on 2008-09-30
Are you sure that the HDD is fine ?

---

### Post by sh4dow_cr4ft on 2008-10-02
The new hard drive is fine, the old hard drive (the one where the image was created from) was faulty.

I imaged the new hard drive from the image taken from the faulty drive.

---

### Post by Sycron on 2008-10-02
This means that you copied the bad sectors to the new hard drive. Did you done a **fsck** scan? If no, open up a terminal and type ```
sudo fsck
```.

---

### Post by sh4dow_cr4ft on 2008-10-02
I did and get the following : 

Resize inode not valid. Recreate<y>?

--------------------------------

I choose yes 
and get:
---------------------------------

Backing up journal inode block information.

/dev/sda5 contains a file system with errors, check forced.

Pass 1: Checking inodes, blocks, and sizes
Group 0's inode table at 8 conflicts with some other fs block.
Relocate<y>?

--------------------------------

I choose yes
and get the same thing but the 8 counts up to 9 and on and on it goes, until it stops for a moment writes to the hard disk, and starts again from the beginning.

---

### Post by Sycron on 2008-10-03
Unmount the partition first and then rescan it. It's ext2/ext3 ?

Type ```
sudo umount /dev/sda5
``` and then ```
sudo fsck
```.

---

### Post by sh4dow_cr4ft on 2008-10-06
The partition is not mounted when I scan, still running into the same problem. Anyone have any ideas of how I can fix this?

---

### Post by Sycron on 2008-10-08
If it's a Windows partition the you have to scan it under Windows.

---

### Post by acidkazak on 2009-01-16
debugfs -w /dev/sda2 -R "features ^resize_inode" 
works for me with the same problem. After this e2fsck runs OK!

---

