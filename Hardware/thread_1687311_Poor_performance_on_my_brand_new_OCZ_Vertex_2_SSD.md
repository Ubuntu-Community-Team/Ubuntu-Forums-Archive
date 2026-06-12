---
title: "Poor performance on my brand new OCZ Vertex 2 SSD"
date: 2011-02-13
forum: Hardware
---

### Post by hernil on 2011-02-13
Hello! 

Just got my new SSD the other day and frankly I'm a little bit disappointed regarding performance. Copying files from one folder to the other on my SSD gives me speeds around the 20MB/sek mark. Tested with 
```
dd if=/dev/zero of=testfil
```
and
```
dd if=/home/hernil/Videos/file.mkv of=/dev/null
```
after a tip on a Norwegian forum which gave me 7.6MB/s read and 65MB/s write respectively. ([link to translated tread]("http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=no&tl=en&u=http%3A%2F%2Fwww.diskusjon.no%2Findex.php%3Fshowtopic%3D1296961&act=url")) 

I found [this]("http://www.ocztechnologyforum.com/forum/showthread.php?79220-Sluggish-peformance-with-Vertex-2-and-Ubuntu-Maverik-Meerkat") tread on the OCZ forums that seems to describe my problem but no solution other than using another kernel. Apparently the problem does not exist in 10.04 but I'm kind of happy on my Meerkat. 

Does anyone have a solution to my problem? I'm open to using a custom kernel if it comes down to that but I'd need some serious help in the process being fairly new to Linux (jumped the Windows ship with Lucid). 

Thank you for all help!

---

### Post by dabl on 2011-02-13
It sure looks like a kernel problem -- OCZ forum is a pretty good place to get that kind of information.

One experiment you could try, to prove the nature of the issue, would be to boot a Live CD of another version or Linux distribution, and do your dd test from there. Two suggestions that come to mind would be (a) daily build ISO of 11.04, and (b) aptosid; both of these have later kernel versions.  For example, if you see with Natty that you don't have the problem, you might just decide to wait the 8 weeks until it is released.

---

### Post by hernil on 2011-02-14
Tested with the Natty daily build which was more up to par with what one would expect. 

Now to the interesting stuff, how do I run the newer kernel on my 10.10 install? :)

---

### Post by dabl on 2011-02-14
> **hernil said:**
> 

Now to the interesting stuff, how do I run the newer kernel on my 10.10 install? :)

Heh heh heh -- well, "interesting" is one characterization of such an adventure.

Seriously, if your productivity environment is important to you, don't try it.  The difference in file transfer speeds cannot possibly be worth the difference between "able to work" and "borked up beyond recovery".  #-o

My other thought is, 11.04, updated as of yesterday, is remarkably trouble-free on my hardware, as far as I have tested it.  If you have 6GB or 8GB free space on your hard drive, why not install today's 11.04 daily build and see if it is stable on your platform?  Install grub to the partition, not the MBR of your hard drive.  In your 10.10 system, run ```
sudo update-grub
``` to put 11.04 on the boot menu.

If your testing indicates 11.04 does everything you need to do, in its current state of development, then just use it, and _do not update it_ until it is released in April.

---

### Post by hernil on 2011-02-14
I'm actually kind of skeptical using Natty as of now. A couple of programs, including Compiz, crashed during my 10 minutes of testing so not really fit for everyday use as of yet. Adding to this, the drastic changes with Unity is something I want to meet in a finished state. Not start off on the wrong foot and hate it for the rest of my time. 

Also tested with Lucid which gave me nice speeds as well so I'm open to downgrading the kernel as well. 

I'll keep the current kernel so I always has that option and if everything gets really ****** up, reinstalling is not that big a deal either (Oh, how I love having a separate home partition ...).  

I'm willing to try. Not getting the most out of my new toy really bugs me!

---

### Post by dabl on 2011-02-14
Well, if you really want to try it ....

I assume (I haven't done it myself) that the process would be:

1. Add the natty main repo to your /etc/apt/sources.list.d/ sources, and sudo apt-get update.
2. sudo apt-get install the linux kernel and image files, including the header files
3. Once you're sure you have what you need, comment out that natty.list file
4. Update initramfs
5. sudo update-grub

6. Use google to see if dabl forgot anything.  ;)

7. Burn some chicken feathers, chant a prayer to the little monkey-god, reboot and see what you have.

Good luck!

---

### Post by hernil on 2011-02-15
I'm still kind of new with all this so it would be great if you could push me in the right direction to find the main repo and correct commands to install the correct files. 

Thanks for all your help so far! It's greatly appreciated! :)

---

### Post by HankB on 2011-02-15
Have you tried any other performance tests? 'dd' probably defaults to a small block size and that may be working against you. You might try adding something like 'bs=4096' to the command line (in the right place - I'm not sure.) You could try other disk benchmarks like iozone or bonnie++.

Thinking of the 4K block size reminds me of another issue. Perhaps the SSE behaves like newer spinning drives that use 4096 byte internal sectors but tell the OS they use the standard 512 byte sectors (for backwards compatibility.) If you don't make the effort to partition on 4096 byte boundaries, performance will be reduced. You might also try different block sizes when you create file systems as that could affect partitions.

I'm not familiar with SSD drives, but these are subjects I would research to get the best benefit out of your SSD. (Apologies if you've already looked into all of this.)

---

