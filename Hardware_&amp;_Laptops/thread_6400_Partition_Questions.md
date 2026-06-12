---
title: "Partition Questions"
date: 2004-11-28
forum: Hardware &amp; Laptops
---

### Post by r0nin on 2004-11-28
First, thank you to those who helped me with my first problems.

I've been running Ubuntu now for a few weeks and have noticed that my /home partition is too small. I made a 3 GB partition for it - Is this enough for a normal user or will this be too small in the long run? I've got about 2GB Amule downloads on it. Though I'd like to move them to a new partition.
My /root partition is sda7, /home sda8, swap sda9 and I've got 100GB free as sda10. It's impossible to merge sda8 & sda10 because the swap is inbetween.
Can I use the empty sda10 partition a personal temp partiton for, docs, the odd download and what else? How can I mount it automagicaly on every boot? And if it's FAT32 I can read it under Win+Linux?

I've also got a 250GB HD (sdb1) on which I'd like to store my Bootlegs. What filesys is recomended under Linux?

What does one actually use the /home partition for? Is it for personal files or additional programmes (like c:\program files in Win) or both?

I used QTParted under Knoppix once to manage my disks, though I always get this error when I start it under Ubuntu (I installed it from Synaptic): *Details: Failed to execute child process "/usr/sbin/su-to-root" (No such file or directory)*

---

### Post by az on 2004-11-28
To run QTParted on debian, where you have a root user as well as other (normal) users, that is the way to start it (sudo-to-root).  In Ubuntu, the command should be 
gksudo qtparted

But it in universe, so you must deal with it as it is.

Your home partition is when all your files are.  You have permission to play around your home directory as you wish.  You do not have permissions to muck about with anything else, unless the permissions are changed.

Asking linux (or any unix) people what is the best way to partition a hard drive is pretty much a religious debate.  It really depends.

1- To make any changes to your partitions, the hard drive must not be mounted.  Use knoppix.  That way, your hard drives are not even needed, so they are not mounted.  If you are running Ubuntu on hda, you can partition hdb by unmounting it.  To play around with hda, you need to chroot into a ramdisk.  It gets ugly, but it is possible...

2-  You can create other partitions and use them for storage.  Do you have another operating system on your computer?  If so, you may want to sacrifice effifiency and use a filesystem both can read and write to (fat32) (aka msdos)
If not, use ext3.  You can use reiserfs (there is always someone who will say they experienced data loss with rieserfs but millions use it.)   If you want stabulity and reasonable speed, ext3.

3-  When these partitions are created, add entries into your /etc/fstab and give your user id permission to read and write to them.  Read up on fstab,  
man fstab
man mount
google search on fstab examples.

4-  You can always just shift your swap down and grow your home partition with qtparted in knoppix,  Make sure you change your fstab, if some partitions are named differently after you finish...

Good luck!!

---

### Post by FLeiXiuS on 2004-11-28
I've always loved 

```
cfdisk
```

Very compact standard partitioner.  You cannot resize current partitions though.

---

### Post by r0nin on 2004-11-29
I've got the HDs partitioned now, they just won't let me write to them.

/dev/sda10      /mnt/temp      ext3      defaults      0      0

That should work, or not? According[this page](http://www.linuxvoodoo.org/resources/howtos/mounting/mounting1.php) it should!
When I change defaults to: users,owner,rw I'll see the HD icon on my desktop, but I only will have root access! I've tried many combinations: user,rw,auto / suid,dev,auto / ... I've never been able to write to the disk though!

---

### Post by r0nin on 2004-11-29
It works with users,umask=000!

---

### Post by FLeiXiuS on 2004-12-01
[QUOTE=r0nin]It works with users,umask=000![/QUOTE]


It'll actually be umask=0000, but since they are all zero's it doesn't even matter.

Remember umask is opposite of chmod.  777 = 000

---

