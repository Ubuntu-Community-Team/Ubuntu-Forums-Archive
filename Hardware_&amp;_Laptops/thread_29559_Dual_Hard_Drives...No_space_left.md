---
title: "Dual Hard Drives...No space left?"
date: 2005-04-24
forum: Hardware &amp; Laptops
---

### Post by phr4gmonk3y on 2005-04-24
I have two hard drives on one IDE channel. One is 160 and has my linux partitions (reiserfs and ext3), and some unallocated space for installing windows when I get around to it. My second drive is 80GB, is formatted ext3, and has all my personal data, music, documents, etc. I can mount the drive successfully, and I can write it it as root. However, applications and the main user on the computer can't write to it, I get an error telling me that the drive is full, when I know I have at least fifteen gigs of space left on it.  Any ideas? Thanks a lot!

---

### Post by nad on 2005-04-24
Less than 10% left on an ext3 file system is not a good thing. You are being warned that administrative measures need to be taken now in order to avoid imminent problems. There is necessary overhead in a journaling filesystem as well as the overhead involved in allocating the space needed to maintain the file system in a "defragged" state.

---

### Post by phr4gmonk3y on 2005-04-24
Should I copy over my data and use a different FS? Would Fat32 work?

---

### Post by nad on 2005-04-24
No, no, no. Journaling file systems are designed to do this. This is a feature, not a bug. You just need more space for more stuff. By the way, what is the output of: df -hl  ?

Continue to use reiserfs or ext3. The overhead in an xfs file system is even greater but it's features are cutting edge, as well as the upcoming reiser4fs.

You should probably also do some file system checking. With the file system unmounted, run the command: e2fsck /dev/your_ext3_filesystem  . You can check the man page for reiserfs to see if there is a similar command.

---

### Post by phr4gmonk3y on 2005-04-24
Here's the output of df -hl

```

michael@zaphod:~$ df -hl
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc1              94G  2.0G   92G   3% /
tmpfs                 380M   16K  380M   1% /dev/shm
/dev/hdc6              19G  1.3G   17G   8% /home
/dev/hdd1              74G   72G     0 100% /mnt/hdd1
/dev                   94G  2.0G   92G   3% /.dev
none                  5.0M  2.9M  2.2M  57% /dev

```

about to check the file system. Thanks!

Edit: df tells me that I'm using 72 Gigs on /dev/hdd1 when I know I'm using only 65.5.

---

### Post by nad on 2005-04-24
[QUOTE=phr4gmonk3y]
Edit: df tells me that I'm using 72 Gigs on /dev/hdd1 when I know I'm using only 65.5.[/QUOTE]

And the obvious question: How do you know this?

---

### Post by phr4gmonk3y on 2005-04-24
Nautilus totals it up at 65.5 GB when I hit properties, also knoppix reads it as not being full last time I checked, and originally, all the data that was in the windows file system was under the space that df tells me it's at.

---

### Post by nad on 2005-04-24
The output of e2fsck gives the fragmentation status of the drive. Did you note this?

Also, remember the overhead I wrote of? The difference you see is due to the actual file sizes being reported in nautilus. The space allocated for them is not. Read the man page for mkfs.ext3 for the particulars. Also note that many of these parameters can be modified to an existing file system with the tune2fs command.

---

### Post by phr4gmonk3y on 2005-04-25
```

michael@zaphod:~$ sudo e2fsck /dev/hdd1
e2fsck 1.35 (28-Feb-2004)
/dev/hdd1: clean, 15223/9781248 files, 18970436/19537040 blocks

```

I'm still a bit confused on the overhead that journaling provides? Could you oblige by explaining, and possibly show me how I could change it?  I'd like to keep journaling, I hear there are benefits, but I'd rather have space on my hard drive.

---

### Post by nad on 2005-04-25
It is not so much the journalling overhead that is causing your problems as much as the block size. A 1k file in a file system with 4k block sizes is going to consume 4k. So a file system containing lots of small files has a lot of wasted space.

The second issue is a fact that you have noticed. By default, 5% of the file system is reserved for the super user. This is why, as root, you are still able to add to the file system.

Edit: Actually, you seem to have a lot of 4M files on this drive. It's time to organize those files. Why don't you move half of them to a new directory called /music in all that free space on your 100G drive, /dev/hdc1.

---

