---
title: "Hibernate fails on fiesty laptop"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by Kralizec on 2007-10-10
I've done some extensive research on this topic and learned a lot about Linux in the process; however, I've not been able to solve the problem.

My problem is that my computer will not hibernate. I've installed uswsusp, reconfigured it numerous times, tried suspend2 for linux... After a failure I check the kernel log and it always reports the same message: 
```

swsusp: Need to copy 114147 pages
swsusp: Normal pages needed: 114147 + 1024 + 20, available pages: 114843
swsusp: Not enough free memory
Error -12 suspending

```
granted, the numbers of pages are not always the same, but the error code is always the same. The odd thing is, before I made another change today, the problem was fairly obvious in that the pages needing to be copied exceeded the available pages. This time, that problem doesn't exist. I'm at a loss for what is still causing the issue and would really like some help. I'll gladly provide information needed.

Thank you in advance.

**Computer specs:**
[LIST]
[*]Gateway MX4664
[*]1 GB RAM
[*]50 GB free HDD space
[/LIST]

---

### Post by cubeist on 2007-10-11
hibernate does not work for a large portion of laptop users.  I doesn't work for me and I gave up trying to get it to work, but even if it did work I wouldn't use it because it takes less time to shutdown and startup than it does to hibernate.  Hopefully hibernate will work better in gutsy for those users who like that... I couldn't care less!

---

### Post by Kralizec on 2007-10-11
I realize that there's a negligible difference between shutdown/startup and hibernate/resume but occasionally I need to leave and don't have the time to save everything I'm doing before leaving, so I would be very grateful for some special assistance with this issue as I think its slightly different from other problems.

---

### Post by Linicks on 2007-10-11
It works fine on my Dell Inspiron 6400 (pre-installed).  Out of interest, how much memory do you have?  How big is your swap file?

Nick

---

### Post by Kralizec on 2007-10-11
I have 1 GB memory; I'm not sure how to find information on my swap file and would greatly like to know how. One of the fixes I found refers to the swap file and I don't know how to find info on it.

---

### Post by Linicks on 2007-10-11
> sudo fdisk -l

Look for the line that has  'Linux swap'  under the System column.

e.g. mine:

```
/dev/sda5             299         619     2578401   82  Linux swap / Solaris
```

Show yours here (I have shown you mine ;-)  )

Nick

---

### Post by Kralizec on 2007-10-11
```
/dev/hda5           11833       12161     2642661   82  Linux swap / Solaris

```

fdisk about my swap file.

---

### Post by Linicks on 2007-10-11
OK, show the output of:

> free

Nick
P.S. I forgot to ask this last post.

---

### Post by Kralizec on 2007-10-11
```
             total       used       free     shared    buffers     cached
Mem:        904248     689596     214652          0      17384     298296
-/+ buffers/cache:     373916     530332
Swap:      2642652          0    2642652

```

>free output

---

### Post by Linicks on 2007-10-11
Ummm, all looks in order - I don't know then.  What is your disk space like?:

> df -h

Nick

---

### Post by Kralizec on 2007-10-11
df -h output:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              90G   36G   50G  42% /
varrun                442M  236K  442M   1% /var/run
varlock               442M     0  442M   0% /var/lock
udev                  442M  108K  442M   1% /dev
devshm                442M   20K  442M   1% /dev/shm
lrm                   442M   33M  409M   8% /lib/modules/2.6.20-16-generic/volatile

```

---

### Post by Linicks on 2007-10-11
I am sorry, but everything looks much like I have - all in order.

I don't know why mine works OK, and yours doesn't.

Bugger.

Nick

---

### Post by Kralizec on 2007-10-11
*sigh* Thanks for trying anyway. You've taught me some good information gathering techniques at the least.

---

### Post by Linicks on 2007-10-11
OK!  Look at this:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88377](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88377)

Nick

---

### Post by cubeist on 2007-10-11
hibernate is so frustrating... but here is a link that might help a bit...  its for opensuse but all the s2disk stuff should translate to ubuntu

[http://en.opensuse.org/S2disk](http://en.opensuse.org/S2disk)

---

### Post by Kralizec on 2007-10-11
Thanks for the links...tried both and no luck.

The first just flat out didn't work. The second link I couldn't completely follow because I couldn't find the package 'pm-utils'...

---

### Post by cubeist on 2007-10-11
> **Kralizec said:**
> Thanks for the links...tried both and no luck.

The first just flat out didn't work. The second link I couldn't completely follow because I couldn't find the package 'pm-utils'...

Hmm... darn, pm-utils is opensuse only at this time... 

here is more reading for you! sorry I only had time to skim through it, but it appears there might be some useful info on page 6
[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

---

### Post by Kralizec on 2007-10-11
On a mere hunch I acquired after reading a few threads, I tested hibernation after disabling Beryl; guess what? It worked perfectly (well, not exactly, resume failed but I figure that was due to the changes I made trying to fix it). However, I would still at some point like to hibernate with Beryl running...

---

### Post by steveneddy on 2007-10-11
I believe the 64 bit version of Feisty has hibernate and suspend working well at this time.

:popcorn:

---

### Post by cubeist on 2007-10-11
> **Kralizec said:**
> On a mere hunch I acquired after reading a few threads, I tested hibernation after disabling Beryl; guess what? It worked perfectly (well, not exactly, resume failed but I figure that was due to the changes I made trying to fix it). However, I would still at some point like to hibernate with Beryl running...

Fantastic!  
I also must turn beryl off in feisty to suspend... but it is such a pain to turn it on and off I have ended up just using metacity all the time.  But the good news is that gutsy beta with compiz works aok with suspend... still no hibernate though...shrug!

---

### Post by phoenix42 on 2007-10-12
> **Kralizec said:**
> On a mere hunch I acquired after reading a few threads, I tested hibernation after disabling Beryl; guess what? It worked perfectly (well, not exactly, resume failed but I figure that was due to the changes I made trying to fix it). However, I would still at some point like to hibernate with Beryl running...

Hi, try adding "resume=/dev/sdaX" to the end of the kernel line in /boot/grub/menu.lst. Replace sdaX with your swap partition.
So it should look something like this:

kernel		/vmlinuz-2.6.22-14-generic root=/dev/sda6 ro quiet splash resume=/dev/sda5

I'm running Gutsy on Dell Latitude D630 and suspend worked from the start, but hibernate just saved the current state but did not resume, until I did this. It also works for me with compiz enabled.

Hope this helps

---

