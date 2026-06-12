---
title: "Swapfile not used &amp; fragmented"
date: 2008-07-27
forum: General Help
---

### Post by dmitrijledkov on 2008-07-27
Swapfile is not used. It is fragmented a bit.

It's fresh installation onto formatted partition. Hybernating button disappeared from the logout/power applet.

How do I defragment it? Or what should I do to make my system use it.

There are a couple bugs on launchpad, but they are concerning Wubi+Swapfiles. One is about swapfile on encrypted partition, but it's not fragmented.


```

sudo filefrag -v /swapfile 
Checking /swapfile
Filesystem type is: ef53
Filesystem cylinder groups is approximately 67
Blocksize of file /swapfile is 4096
File size of /swapfile is 2147483648 (524288 blocks)
First block: 120832
Last block: 1570599
Discontinuity: Block 6137 is at 131329 (was 126975)
Discontinuity: Block 6144 is at 164639 (was 131335)
Discontinuity: Block 6145 is at 172092 (was 164639)
Discontinuity: Block 6149 is at 192513 (was 172095)
......
/swapfile: 794 extents found, perfection would be 17 extents

dmitrij@dmitrij-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1003676     693064     310612          0      17732     329532
-/+ buffers/cache:     345800     657876
Swap:      2097144          0    2097144
dmitrij@dmitrij-laptop:~$ 

dmitrij@dmitrij-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1003676     991236      12440          0      18920     374120
-/+ buffers/cache:     598196     405480
Swap:      2097144          0    2097144

```

---

### Post by Potatoj316 on 2008-07-28
i think you can run a command to turn your swap on and off.  Im pretty sure swapoff is the command to turn your swap off so try swapon to turn it on.

---

### Post by bodhi.zazen on 2008-07-28
I do not think hibernation works well with wubi. One problem, it seems, is you need a swap partition rather then a swap file.

Second, your swap is working just fine. Swap is used after RAM and you still have free RAM ....

FYI Linux is not windows. You do not need to defragment Linux file systems. Also Linux uses RAM very different then Windows.

RAM : [http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

So I think the short answer to your hibernation problem is to use a standard installation, make your swap partition just a little larger then your RAM.

---

### Post by dmitrijledkov on 2008-08-15
> **bodhi.zazen said:**
> I do not think hibernation works well with wubi. One problem, it seems, is you need a swap partition rather then a swap file.
I'm not using wubi. I have installed into two partitions: / and /home.

> **bodhi.zazen said:**
> 
Second, your swap is working just fine. Swap is used after RAM and you still have free RAM ....
I thought the idea was that you should always use 2xRam for swap so that your system would be optimised, e.g. use swap where appropriate. Are you saying swap is now useless since new computers have 1G+ ram?

> **bodhi.zazen said:**
> 
FYI Linux is not windows. You do not need to defragment Linux file systems. Also Linux uses RAM very different then Windows.[QUOTE]
Hmmm, saw somewhere in the ubuntuwiki, that you should make sure that swapfile is continues hense special command (as far as i remember dd from /dev/null)
[QUOTE=bodhi.zazen;5476395]
RAM : [http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)
thanks for good info!
> **bodhi.zazen said:**
> 
So I think the short answer to your hibernation problem is to use a standard installation, make your swap partition just a little larger then your RAM.
Hmmmm, pretty standard for intel mac, first 2 partitions used by mac os x. 2 left for playing around. I made those into / and /home.

---

### Post by bodhi.zazen on 2008-08-15
Cheers.

Yes, the "old rule" that swap size should be ram X 2 is outdated. People generally say max is 1 Gb. Some people are starting to advise a max swap size of 512 Mb.

Swap is basically space on the HD to be used if you run out of RAM and , IMO, your system is optimized already.

---

