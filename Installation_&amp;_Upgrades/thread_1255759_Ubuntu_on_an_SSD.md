---
title: "Ubuntu on an SSD"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by CaesarLike on 2009-09-01
HI there,

I want to install Ubuntu to an SSD, are there any things I need to know or consider when doing so?
Not putting the swap on the SSD is one I know of.  What about reducing the number of writes to the drive by the OS?
Any suggestions for a suitable file system?  Ext2 maybe?

---

### Post by tommcd on 2009-09-02
Some people have recommended that the ext2 file system should be used on SSD drives instead of ext3 (or the newer ext4) in order to reduce the number of writes to the drive so as to not prematurely wear out the SSD drive. However, this article from linux kernel developer Theodore Tso says it is really not necessary:
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
The bottom line:
 You can install ubuntu on an SSD drive using ext3 or ext4. Just change the boot option for Ubuntu in the /etc/fstab file from **relatime** to **noatime** as discussed in the article. This also (theoretically at least) will give a slight performance boost. I have booting all my linux distros with the noatime boot option and I have never had any problems with it. I can't say I notice any performance increase though. See "man mount" for more info on the noatime boot option:
> noatime
              Do not update inode access times on this file system (e.g, for faster access on the news spool to speed up news servers).


---

### Post by Mighty_Joe on 2009-09-02
> **tommcd said:**
>  this article from linux kernel developer Theodore Tso says it is really not necessary:


Well, he concludes that there IS an added overhead to journaling, but at 4-12%, it isn't large. I run Ubuntu on a USB flash drive.  With USB a serious bottleneck on throughput, I could use a 4-12% improvement!
Have a look at my post in [this topic]("http://ubuntuforums.org/showthread.php?t=1193680") for some other pointers on improving performance on flash drives, like moving logging and cache to tmpfs.

---

### Post by tommcd on 2009-09-03
> **Mighty_Joe said:**
> Well, he concludes that there IS an added overhead to journaling, but at 4-12%, it isn't large. 
The point I was making is that ext3 should not wear out the SSD prematurely. Anyway, he goes on to say that:
> First of all, for normal workloads that include data writes, the overhead from journaling is actually relatively small (between 4 and 12%, depending on the workload). Further, than **much of this overhead can be reduced by enabling the noatime option**, with relatime providing some benefit, but ultimately if the goal is to reduce your file system&#8217;s write load, especially where an SSD is involved, I would strongly recommend the use of noatime over relatime.
That is why I suggested changing the default relatime to noatime in Ubuntu's fstab.

---

### Post by CaesarLike on 2009-09-07
Thanks everyone for the adivice.

Does anyone know if Ubuntu correctly aligns the partitions for the SSD drive?  I know Win XP does not, and that Win7 does.  I have read somewhere that at this time linux distros do not, and that it is only win7 that does.  Is this correct?

---

### Post by tommcd on 2009-09-08
> **CaesarLike said:**
> 
Does anyone know if Ubuntu correctly aligns the partitions for the SSD drive?  I know Win XP does not, and that Win7 does.  I have read somewhere that at this time linux distros do not, and that it is only win7 that does.  Is this correct?
Yes, you are correct. As I discovered with some googleing after I read your post, linux does not align partitions correctly for maximum efficiency on SSD drives. There are apparently ways to fix this though. Enter Theodore Tso to the rescue again:
[http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/](http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/)
Also see the step by step guide here:
[http://www.ocztechnologyforum.com/forum/showthread.php?p=373226#post373226](http://www.ocztechnologyforum.com/forum/showthread.php?p=373226#post373226)

---

