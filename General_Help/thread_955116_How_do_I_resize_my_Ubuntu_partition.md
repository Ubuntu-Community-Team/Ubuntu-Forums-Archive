---
title: "How do I resize my Ubuntu partition?"
date: 2008-10-21
forum: General Help
---

### Post by damijit on 2008-10-21
Hello, I've been using Ubuntu for about 2 months on a laptop with a tiny hard drive (about 35GiB). I gave it a pretty small partition (about 7GiB) while I tried it out, but now I'm confident I want to keep using it long term. I went to the partition editor under System > Administration, but I couldn't find an option for shrinking the Windows partition (in fact, gparted can't tell how much of it is used--I know there are about 4.5GiB free). Getting rid of Windows entirely isn't an option for a couple reasons, I just want to resize the partition.

Can anyone help me out?

---

### Post by shawnrgr on 2008-10-21
Your going to have to resize both partitions yes? Decrease the windows partition and give the extra space to ubuntu?

first boot into windows and run defrag (you should always defrag a fat32/ntfs partition before resizing. 

then boot up with ubuntu live cd. You need to do this because gparted can't resize a partition if its currently mounted.

you should then be able to resize both partitions accordingly. save changed and apply to windows partition, then move on and increase ubuntu.

---

### Post by damijit on 2008-10-22
Well, I shrunk my Windows partition, but I'm having trouble growing the Ubuntu partition.

There are two partitions: The main one, and the linux swap partition, both inside an "extended" partition. It won't let me grow the extended partition because it says the swap partition is mounted.

This is while running from the live CD.

How do I keep the swap partition from getting mounted?

---

### Post by shawnrgr on 2008-10-22
You don't have to resize the swap partition, most likely your not even really using it, but DON'T remove it. Just resize the ubuntu partition

EDIT:

i can't be positive this unmounts it but try anyway

```
swapoff
```

---

### Post by damijit on 2008-10-22
To clarify: I am not trying to resize the swap partition. This is what my drive looks like

[windows and other stuff       ["extended"[ubuntu][linux swap]] ]

the "extended" section has no free space, so it needs to be increased to increase the size of the ubuntu partition. However, it won't let me increase it because the "linux swap" portion is mounted.

I'll try swapoff and see if that works, just wanted to clarify the problem.

---

### Post by damijit on 2008-10-22
Uh oh.
It got most of the way through growing it, then gave me an error (see attached)

I'm running from the hard drive right now (I can't connect to the internet from the live cd), so it's not a fatal problem, but:
Instead of having about 5 GiB used and 1.5 free on a 6.5 GiB partition, I have 7.5 GiB used and 1.5 free on a 9 GiB partition. What's the deal?

I'm attaching the log:
Nevermind, it won't let me upload .htm files. Here is the part that gave an error:

```

grow filesystem to fill the partition  00:01    ( ERROR )
     	
resize2fs /dev/sda5
     	
resize2fs 1.40.8 (13-Mar-2008)
Please run 'e2fsck -f /dev/sda5' first.
```

---

### Post by Elfy on 2008-10-22
Boot the livecd and run the command from a terminal

```
sudo e2fsck -f /dev/sda5
```

---

### Post by damijit on 2008-10-22
OK, I completed that, but my partition is still bloated.

---

### Post by Elfy on 2008-10-22
Boot the livecd and run partition editor. Make sure you have backups.

Shrink the win partition, apply
Right click the swap partition and unmount
Grow the extended partition, apply
Grow the ubuntu linux partition, apply

Close and reboot

---

### Post by damijit on 2008-10-22
That is what I've tried to do, I just got an error on the last step.

---

### Post by Elfy on 2008-10-22
Not sure then, if you get an error again then maybe there is a problem with the hard drive.

Make sure that the drive is unmounted, ```
df -h
``` will tell you what is mounted, then check the partiton with

```
e2fsck -v -n -f /dev/sda5
```

---

### Post by damijit on 2008-10-22
Thanks, but I've already done that (well without the -v and -n options).
3 disappearing GiB is sort of a big problem on a drive this small...

---

### Post by Elfy on 2008-10-22
Indeed I'm sure it is but if you can't help people help you then ...

The command will run in a differnt mode, this time it will force the check whether the drive is clean or not (-f) and answer no to any questions (-n) and be verbose (-v)

It appears that there is something wrong with the drive and it would be good to know for certain.

---

### Post by damijit on 2008-10-22
I'm sorry for being difficult--I was thinking you didn't realize I had performed that command. Here are the results with the new parameters:

```
ubuntu@ubuntu:~$ sudo e2fsck -v -n -f /dev/sda5
e2fsck 1.40.8 (13-Mar-2008)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  177347 inodes used (40.57%)
    1993 non-contiguous inodes (1.1%)
         # of inodes with ind/dind/tind blocks: 9191/117/0
 1340307 blocks used (76.72%)
       0 bad blocks
       1 large file

  138192 regular files
   19081 directories
      69 character device files
      26 block device files
       2 fifos
     392 links
   19962 symbolic links (18742 fast symbolic links)
       6 sockets
--------
  177730 files

```

Thank you for your (donated) time!

---

### Post by Elfy on 2008-10-23
mmm not sure - that looks ok to me.

Two things here - lost space and resizing

First - donwload and burn [partedmagic]("http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads") - burn as an iso and boot with it - I have had problems with versions of gparted in the past, and try the resize from there.

Second - check for files in trash, both yours and roots - [http://ohioloco.ubuntuforums.org/showthread.php?t=898573](http://ohioloco.ubuntuforums.org/showthread.php?t=898573)

---

