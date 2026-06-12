---
title: "help please! partition magic screwed my ext3"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by djdjules on 2007-06-10
Hello I'm Jules

This is what happened:

The hard disc in my laptop WAS partitioned as follows

[NTFS][[ext3][fat32][swap]][other]

Since I upgraded from edgy to feisty now I was able to write onto the NTFS from ubuntu.
So I thought it would be OK to get rid of the fat32 partition (which I used to transfer files between win and ubuntu)

I used partition magic 8 to delete the fat32 partition and now my HD looked like this

[NTFS][[ext3][       ][swap]][other]

next I told partition magic to move the ext3 partition "to the right" so that i could later resize the windows partition.

I wanted my HD to look like this

[NTFS][[       ][ext3][swap]][other]

but once partition magic "finished moving" I tried rebooting and GRUB said       Error 17

I thought that I would only have to update grub to fix the problem 
but after a few tries with the Super Grub Disc I could not get ubuntu to boot.

Using SGD I booted windows and checked the status on Partition Magic 
and found that instead of having my HD look like this

[NTFS][[       ][ext3][swap]][other]

it looked like this

[NTFS][[       ][ext2][swap]][other]

Partition Magic 8 just changed my ext3 to ext2 on its own.

Is this the first time this happens?
Are my files really lost?

help will be greatly appreciated

---

### Post by neptho on 2007-06-10
EXT2 and EXT3 are the same partition type; it may not recognize that it's actually EXT3.  If this is the case, you may have damaged some files if it was not shutdown properly.

However, if the journal is replayed, and everything is 'OK', you should be fine to temporarily mount it as an ext2 partition.  Run fsck on it, then fix your offsets (Looks like your ext3 is now /dev/sda3 or /dev/hda3 instead of /dev/sda2 /or /dev/hda2.  You'll have to edit your menu.lst (hit esc to go into grub,  go to 'repair' mode, then change root=/dev/X...' and 'b' for boot into it.  Then, edit /etc/fstab.

---

### Post by djdjules on 2007-06-11
I havent been able to boot ubuntu to edit stuff using the Super Grub Disc

I will your suggestion tomorrow with a fresh liveCD

If I find that my files where deleted by partition magic I will be very upset
and will have to spend a long day reinstalling linux

---

### Post by djdjules on 2007-06-13
i tried booting the slax liveCD and it just hanged
so i went over to my friends place and used his Ubuntu liveCD and this one worked (way to go ubuntu)

ubuntu detected sda5 (the partition with the problem) 
but didnt mount it. 
I tried to fsck sda5 but it could not be performed. it said that the superblock was corrupted or something

any ideas?

---

### Post by djdjules on 2007-11-22
anyone got info on these subject?

---

### Post by BrownCoal on 2007-12-30
Why partitionmagic made the ext3 into ext2 I don't know, suffice to say that they are interoperable, so, whilst that is unusual, it didn't wreck anything and it's easy to change it back to ext3. The only real difference between ext2 and ext3 is that ext3 has journaling. Journaling basically means you don't have to wait for a full disk scan after a crash like you would with ext2. It's the same when going from microsofts FAT32 to NTFS; FAT32 has to do a long scan after a crash and NTFS doesn't.

See my next post for the (hopefully) solution.

---

### Post by BrownCoal on 2007-12-30
For the most common GRUB error, what you need to know here is that at the very start of every HDD is a small piece of data called the "Master Boot Record" (MBR). It holds the information about all the partitions, their size, location etc.. For GRUB to work it needs to two things 1.to  be written to the MBR 2. know where the file "menu.lst" is located on the HDD. menu.lst holds all the data that GRUB needs and is located on the same partition as Linux, this is because the MBR has a small, unchangeable size. Unfortunately, the GRUB data is static i.e. it doesn't get updated with the rest of the MBR data when you move, resize or otherwise change any partitions.

(in this example, partition three is the Linux partition, you can check what partition yours in on by installing the "gparted" program, or burn the gparted liveCD from here: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php))
So say I have 3 partitions, numbered as 0, 1 and 2 (GRUB starts counting from zero). I then install Ubuntu to partition 2 (the third one). All works fine. Now say I decide to delete partition 1 (the second partition) to make more room for Linux, well, all of the partition data is updated in the MBR, but the GRUB data  is static and only a purpose-built program will know what to do to change it. Buy deleting the middle patition, partition 2 technically becomes partition 1. As the GRUB data is static it still states that "menu.lst" is on partition 2, but now there is no partition 2! All GRUB can do in this situation is give you an error message, and you can't start any OS that is on the HDD.

One option is to undo the partition change/rearrangement buy recreation the middle partition in the same position. It doesn't have to be the same size, just as long as Linux becomes the third partition again.

If we really want to only have two partitions though we actually have to update the MBR GRUB data to state that menu.lst file  is now located on the second of two partitions. If you installed Ubuntu you probably know how to boot Ubuntu from the liveCD, if not see here:[https://help.ubuntu.com/community/BootFromCD?highlight=%28from%29%7C%28boot%29](https://help.ubuntu.com/community/BootFromCD?highlight=%28from%29%7C%28boot%29). Now that Ubuntu is loaded we can run the GRUB program from a the command-line to update it on the MBR.

1. start Terminal (Applications>Accessories>Terminal)
2. type "sudo grub" (ignore all quotation marks)
3. type "find /boot/grub/stage1". The output should look similar to this: hd0,5
4. type "root (hd?,?)". The contents of the brackets should correspond to the previous output (the brackets must be typed as well).
5. type "setup (hd0)"
6. type "quit"
7. restart

The GRUB menu should now be recovered. I've done this many many times, but I don't know it by heart, so if you get an error in the command-line then try google to resolve the error.

Well I hope this guide has fixed your problem and taught you a little about the workings of the MBR. If it has then you might like to spend a few minutes to point other people with this problem to this guide (it's a very common beginners problem). Just do a search of the latest forum threads with the keywords "GRUB" and/or "boot.

HOPE YOU CAN ENJOY UBUNTU TOO!

---

