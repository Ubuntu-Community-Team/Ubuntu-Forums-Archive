---
title: "Trim: Windows + Ubuntu on ssd, is Ubuntu trimmed too?"
date: 2010-03-17
forum: Hardware
---

### Post by monkman on 2010-03-17
i have vista + ubuntu installed on one ssd(intel x25-v) drive.

I wonder weather my ext4 partition is beeing trimmed too, when running the intel toolbox trim on vista. since i don't know exactly how the trimming works.

thx!

---

### Post by harakiri on 2010-03-29
Hi monkman,

I am also pretty new to the concept of Ubuntu on SSD. I am awaiting the delivery of Intel X25-M 80G. During the wait period I did some reading and IMHO the answer to your question is no. TRIM is a OS feature. What I mean to say is the OS is supposed to tell the SSD what pages are invalid so that the drive can erase them.

So I believe that your ext4 is not being trimmed. Google for hdparam & wisher. Maybe they can help you. But they require 2.6.33 kernel i suppose. Please do confirm from other senior members of the forum before you do anything.

Harakiri

---

### Post by nicedream on 2010-04-01
Hi - 
To answer your specific question, I doubt that anything in the Linux ext4 partition will be trimmed.  For that to happen, Windows would need to be able to read the ext4 filesystem table in order to tell the drive which blocks on the disk are no longer in use.  As far as I know, Windows does not have read support for ext4.

The issue of TRIM support in Linux is pretty new, so when I recently got my Intel Solid State drive I had a hard time finding any information on what exactly I needed to do to in order to enable the TRIM feature.  TRIM support was added in kernel 2.6.33, and as far as I know there is no Ubuntu-provided kernel at this version level.  I'm not sure what kernel 10.04 will bring, or if Ubuntu will backport TRIM support into any kernels earlier than 2.6.33.  Regardless, compiling your own kernel is always an option :)

After a lot of research, I compiled a 2.6.33 kernel and successfully enabled TRIM for my Intel SSD.  I wrote a quick how-to on enabling TRIM in Linux.  Hopefully it will be helpful for you (or anyone else jumping into the SSD pool)

[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/]("http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/")

---

### Post by fjf on 2010-04-01
Thats a nice howto.  Compiling the kernel is not necessary, you can get it here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by cascade9 on 2010-04-01
I'm pretty sure I read somewhere on these forums that the 2.6.32 kernel is having TRIM support added. 

Mainly because 2.6.32 is going to be used by several distros that are plannign on using them long-term, and TRIM support (and i3, i5 and i7 steppings) is going to become commonplace during the 2.6.32 kernels lifespan.

---

### Post by nicedream on 2010-04-01
> **fjf said:**
> Thats a nice howto.  Compiling the kernel is not necessary, you can get it here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Thanks for the kind words.  I'm not really an Ubuntu user, so I don't keep up with their kernels.  Good to see that the most recent ones are available.

---

### Post by fjf on 2010-04-02
I might get an intel G2 soon.  Could you add some words in your howto about partition alignment using gparted?.  I found no clear indications on how-to do it, and I would not like using a windows 7 disk to partition the disk it (as most people seem to be doing).

Thanks.

---

### Post by PatrickVogeli on 2010-04-02
so Trim works on linux.. nice. Once I can get the Kingston SSD 64GB Value Drive for under 100&#8364; I think I'll jump into the SSD crew too.

---

### Post by nicedream on 2010-04-02
> **fjf said:**
> I might get an intel G2 soon.  Could you add some words in your howto about partition alignment using gparted?.  I found no clear indications on how-to do it, and I would not like using a windows 7 disk to partition the disk it (as most people seem to be doing).

Thanks.

You know, partition alignment is one thing that I missed when I was doing my research.  Now that my drive has been formatted and the OS has been configured, it might be a while before I look into re-aligning the partitions.

Just yesterday I was reading a pretty good guide on the subject, but I can't seem to find it now.  I'll post it back in this thread if I do....

---

### Post by jznomoney on 2010-04-14
so when you go here [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
which files do you download?  How do you get ubuntu to boot with the new kernel?

---

### Post by jznomoney on 2010-04-15
nm i figured it out.  I didn't install the deb file.  Anyways, one i boot into the new kernel is trim automatically enabled or are there any other commands to enable it?

---

### Post by nicedream on 2010-04-15
> **jznomoney said:**
> nm i figured it out.  I didn't install the deb file.  Anyways, one i boot into the new kernel is trim automatically enabled or are there any other commands to enable it?

Check my link above for instructions on how to enable TRIM.

---

### Post by jznomoney on 2010-04-15
So what you are saying is that even with the new kernel you have to manually set it to trim.  It's not like windows 7 where the os passes it to the ssd drive?

---

### Post by nicedream on 2010-04-15
> **jznomoney said:**
> So what you are saying is that even with the new kernel you have to manually set it to trim.  It's not like windows 7 where the os passes it to the ssd drive?

The OS does pass the command to the drive - it's just not enabled by default.

---

### Post by spoon_ on 2010-04-21
Is there any reason to disable the ext4 journal besides paranoia about drive lifespan? Will TRIM still work with the journal enabled?

---

### Post by nicedream on 2010-04-21
> **spoon_ said:**
> Is there any reason to disable the ext4 journal besides paranoia about drive lifespan? Will TRIM still work with the journal enabled?

Trim will still work with the journal enabled.  Disabling the journal just extends the drive life (in theory at least), and also provides a very slight performance boost.

---

### Post by spoon_ on 2010-04-21
> **nicedream said:**
> Trim will still work with the journal enabled.  Disabling the journal just extends the drive life (in theory at least), and also provides a very slight performance boost.

Thanks for the quick reply!

---

### Post by robbel on 2010-04-30
TRIM doesn't work in the 10.04 kernel 2.6.32 yet: [https://bugs.launchpad.net/bugs/571476](https://bugs.launchpad.net/bugs/571476)

The wisher scripts that are floating around with hdparm also do not work with intel x25-m under 2.6.32 (even after the intel patch to limit to 512kb TRIM). This can be verified with the same test from the gentoo forums mentioned in the bug report above.

So basically, there is no support for any sort of trim, either manual or automatic, under 10.04 with the Intel SSD now.

---

### Post by nicedream on 2010-04-30
> **robbel said:**
> TRIM doesn't work in the 10.04 kernel 2.6.32 yet: [https://bugs.launchpad.net/bugs/571476](https://bugs.launchpad.net/bugs/571476)

The wisher scripts that are floating around with hdparm also do not work with intel x25-m under 2.6.32 (even after the intel patch to limit to 512kb TRIM). This can be verified with the same test from the gentoo forums mentioned in the bug report above.

So basically, there is no support for any sort of trim, either manual or automatic, under 10.04 with the Intel SSD now.

One of the earlier posts in this thread listed where to get alternate kernels (including 2.3.33).

Also, there is a wiper-intel.sh script floating around that works for the Intel SSDs.  Do a google search and you'll find it.

---

### Post by robbel on 2010-04-30
> **nicedream said:**
> Also, there is a wiper-intel.sh script floating around that works for the Intel SSDs.  Do a google search and you'll find it.

I tried the wiper-intel script under ubuntu 10.04. It goes through but does not clean up the correct parts of the ssd. it's buggy.

In the bug report above, I put a link to the gentoo forums on how to test whether TRIM is working. I performed the same test with 2.6.33 (it works) and with the wiper scripts under 2.6.32 (it doesn't clean up correctly).

The original author of the script also mentions that it's buggy and stopped development of it: [http://www.ocztechnologyforum.com/forum/showthread.php?60882-wiper.sh-discussion-thread-(Linux-TRIM-tool)/page16](http://www.ocztechnologyforum.com/forum/showthread.php?60882-wiper.sh-discussion-thread-(Linux-TRIM-tool)/page16) (see post 234).

So the only option for now seems to upgrade to 2.6.33 with all its annoyances under Ubuntu (e.g. unsupported nvidia driver install, ..). I hope TRIM support is eventually backported into the 2.6.32 line for official ubuntu support (that's what my bug report is about).

---

### Post by ariel on 2010-05-25
> **robbel said:**
> I tried the wiper-intel script under ubuntu 10.04. It goes through but does not clean up the correct parts of the ssd. it's buggy.

In the bug report above, I put a link to the gentoo forums on how to test whether TRIM is working. I performed the same test with 2.6.33 (it works) and with the wiper scripts under 2.6.32 (it doesn't clean up correctly).

The original author of the script also mentions that it's buggy and stopped development of it: [http://www.ocztechnologyforum.com/forum/showthread.php?60882-wiper.sh-discussion-thread-(Linux-TRIM-tool)/page16]("http://www.ocztechnologyforum.com/forum/showthread.php?60882-wiper.sh-discussion-thread-%28Linux-TRIM-tool%29/page16") (see post 234).

So the only option for now seems to upgrade to 2.6.33 with all its annoyances under Ubuntu (e.g. unsupported nvidia driver install, ..). I hope TRIM support is eventually backported into the 2.6.32 line for official ubuntu support (that's what my bug report is about).

did you get the wiper.sh (or wiper-intel.sh) script to really work with intel ssd's under 10.04 / 2.6.32 (amd64)? all I am getting are errors: "FAILED: Input/output error" 

If you have a working wiper.sh for intel / ubuntu lucid amd64, do you mind posting it?

---

