---
title: "Need large hdd partitioning advice."
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by Baasha on 2009-09-28
I have just built a brand new system with an i5-750 cpu and a 1Tb hard drive.  I have read a lot of articles about Linux partitions but they all seem a little dated.  With 1Tb of room I am a little unsure of how big to make the partitions.

On my old system 32 bit Ubuntu 8.04 I had an 8Gb / but after several version upgrades the system got clogged up.  So on my new 64 bit Jaunty I was thinking of using 15-20 Gb and about 2 Gb for a swap partition.  I know the rule of thumb is make swap twice the ram size but I have 4 Gb of ram.  Will I ever need more than 2 Gb of swap?

I was also thinking of leaving some room on the drive (in case I don't like the 64 bit version) to install a 32 bit verion.  Although I think it unlikely that I won't like the 64 bit, this may be a wise thing to do.

I am looking for comments or suggestions from other large drive users.  For instance, I am definitely going to have a separate home partition, but is it worth while having separate partitions for /usr, /var, and /tmp?  If so, how big should they be?  I know I have lots of space but there is no point wasting it either.

I welcome any and all comments on the above.

---

### Post by raymondh on 2009-09-28
> **Baasha said:**
> I have just built a brand new system with an i5-750 cpu and a 1Tb hard drive.  I have read a lot of articles about Linux partitions but they all seem a little dated.  With 1Tb of room I am a little unsure of how big to make the partitions.

On my old system 32 bit Ubuntu 8.04 I had an 8Gb / but after several version upgrades the system got clogged up.  So on my new 64 bit Jaunty I was thinking of using 15-20 Gb and about 2 Gb for a swap partition.  I know the rule of thumb is make swap twice the ram size but I have 4 Gb of ram.  Will I ever need more than 2 Gb of swap?

I was also thinking of leaving some room on the drive (in case I don't like the 64 bit version) to install a 32 bit verion.  Although I think it unlikely that I won't like the 64 bit, this may be a wise thing to do.

I am looking for comments or suggestions from other large drive users.  For instance, I am definitely going to have a separate home partition, but is it worth while having separate partitions for /usr, /var, and /tmp?  If so, how big should they be?  I know I have lots of space but there is no point wasting it either.

I welcome any and all comments on the above.

-20GB for root is nice.
-2GB for SWAP is OK.  But with that much space, why not make 1x maximum installable RAM (just in case you upgrade later on).
-I find no need for /var unless you have a server and need to view logs regularly.
- /usr depends on your requirements.
- If you plan to multiboot with other distros' (or OS'), I think a /data is better than a /home as different config files may cause havoc.  Besides, you can always back-up /home to /data.
-  I'm sure your BIOS is up to date.  Just note that a HD that big and if you run into error 18, you might want to start considering a /boot.  It only requires so little space in front of the drive (250MB is good enough).  

As you know by now, Ubuntu does not require it to be in a primary partition.  Extended is fine.  If you do put a /boot, make that primary.  The rest of Ubuntu can be logicals inside an extended.

Have fun and happy ubuntu-ing.  Enjoy your new system :)

Regards,

---

### Post by Baasha on 2009-09-28
Thanks for your comments Raymond.

You mentioned having a /data partition, which I was thinking about anyway, but that brings up another question.  What would be a prudent size for a /home partition if it is no longer going to be holding all my personal files?

At the moment this is what I am thinking about:
/      20 Gb
/swap   4 Gb
/home   ?
/data 500 Gb

I am beginning to wonder why I bought such a big hd but the price was just too good to pass up :-))

---

### Post by raymondh on 2009-09-29
> **Baasha said:**
> Thanks for your comments Raymond.

You mentioned having a /data partition, which I was thinking about anyway, but that brings up another question.  What would be a prudent size for a /home partition if it is no longer going to be holding all my personal files?

At the moment this is what I am thinking about:
/      20 Gb
/swap   4 Gb
/home   ?
/data 500 Gb

I am beginning to wonder why I bought such a big hd but the price was just too good to pass up :-))

Baasha,

/home .... although no longer holding your personal data/media ... will still hold config files and settings.  That is nice to retain should a re-install be required in the future.  I think 30GB is ok for /home in this scenario.

Regards,

---

