---
title: "Both cores on Dual Core not being used."
date: 2006-10-14
forum: Hardware &amp; Laptops
---

### Post by AmbigFish on 2006-10-14
Hey guys, I have come to realize that both cores on my Intel Core Duo processor are not being used. I read about needing SMP, but when I looked in synaptic, nothing related to SMP was installed. I then clicked on different versions of it, and all I saw was ones for AMD's K7 architecture, and ones for Intel processors, all the way up to the P4, but nothing for any mobile processors or one for Intel Core Duo processor.

Laptop Specs:

Intel Core Duo 2.0 ghz Processor
2 Gigs of DDR2 RAM
ATi Mobility x1400
120 gig HDD (60 Partitioned for Windows and 60 for Ubuntu, so yes, I am dual booting).


Please help me. I also want to clearify, a Intel Core Duo is not the same as a Pentium D processor and is not the same as the Intel Core 2 Duo processors.

Thank you.

---

### Post by eggdeng on 2006-10-14
Would be interested to know what made you realize that.

---

### Post by AmbigFish on 2006-10-14
I was just interested, so I went to System monitor and it only showed one CPU. On another post here from earlier this year, a guy posted his from a Pentium D processor, and it actually shows both CPUs, where as mine is only showing one and I have essentially two. However, that post never really answered the question though.

---

### Post by Frogger on 2006-10-14
The problem is you are not running an SMP (multiprocessor) Kernel.
To upgrade to an SMP Kernel you can do one of two things:
Recompile your kernel, I would not recommend this, but if you want to there are some great guides on this forum.
Or
Install a SMP Kernel Binary.  This is what I would recommend.  Your Core Duo is base on the Pentium III arch, meaning it will run best with the 686 kernel.
Here is how you do this, its not hard at all:
Open Synaptic
Mark the linux-686-SMP package (and its dependancies)
and click apply.

(From your post I am guessing you don't need the Synaptic walkthrough but just in case someone searches for this problem later, I offered it)

The important thing to note is that the Core Duo is based on the 686 instruction set.

I hope that solves it.

---

### Post by AmbigFish on 2006-10-17
Thank you very much, it did help and it appears to work. Sorry for the late response, real life gets in the way sometimes.;)

---

### Post by arthur24b6 on 2006-11-14
I had this problem as well with a pentium d and the generic kernel. I was having hda interupt errors. Looking at this post: [http://ubuntuforums.org/archive/index.php/t-394.html](http://ubuntuforums.org/archive/index.php/t-394.html)

That adding: noapic pci=usepirqmask to grub would help.

This proved true. Interestingly, changing my machine to a single processor in the bios also solves the problem, but obviously that isn't a long term solution. 

So fyi, on an emachines t5212 dual core, noapic pci=usepirqmask is necessary for getting both cores to run.

---

### Post by Elaztic on 2006-11-14
Edgy has native support for multi cpus or cores.
I have a Dell D820 with Intel core duo.
After I upgraded from Dapper to Edgy it did not work.
After installing 'linux restricted modules' through synaptic it worked.
NB: I am using the generic kernel.

---

### Post by flyingsolo on 2006-11-21
I have dapper 686-smp running on dual core but only one of cores is recognized.  Is there something I have to do to tell system to seek 2nd core since I upgraded from 386 kernel to the current one? (right now, system monitor shows one core going up to to 2GHz)
thanks

---

### Post by Tumpster on 2007-07-07
I have the same problem, I'm running the 686 kernel now and still see only one cpu core?

---

### Post by eggdeng on 2007-07-08
Check your kernel version with ```
uname -a
``` As you are using Dapper, you need to install the SMP kernel, either with  ```
sudo apt-get install linux-image-686-smp
``` or via Synaptic as in Frogger's post above. (You will probably have to reinstall your video drivers.)

---

### Post by Tumpster on 2007-07-26
I need further help:

craig@craig-desktop:~$ uname -a
Linux craig-desktop 2.6.15-28-686 #1 SMP PREEMPT Wed Jul 18 22:57:30 UTC 2007 i686 GNU/Linux
craig@craig-desktop:~$ sudo apt-get install linux-image-686-smp
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-image-686-smp
craig@craig-desktop:~$

---

### Post by eggdeng on 2007-07-28
My bad, should have been
```
sudo apt-get install linux-686-smp
```
I don't think it will help any though, because you seem to have the SMP kernel already.

---

### Post by xghstst0riesx on 2007-08-07
I also have only one core detected. This is the output of uname: 
"Linux patrick-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux"

I have a Dell E1505. I am thinking the video card may have something to do with it. I have the ATI Mobility Radeon X1300 and have the proprietary ATI driver installed. Does anyone have any ideas what else could be causing this?

---

### Post by last1 on 2007-09-10
I'm also having problems, since I upgraded the system to Gutsy today. Though my hardware list still shows it as a core2duo, top no longer lists both cores and it is more sluggish. Both cores were working fine in Feisty with any kernel that was being used, but now they're not. 

When I tried to install the above listed smp kernel, I get this

linux-686-smp:
  Depends: linux-image-generic (=2.6.20.15.14) but 2.6.22.11.12 is to be installed

That transition package points to the same kernel I already had, no special SMP letters in its title, just an older version of the kernel which was installed when I upgraded.
The 2.6.22 kernel is what uname shows right now, which was installed when I upgraded. Is there something wrong with this kernel? Why doesn't the generic kernel work with dual cores like the generic 2.6.20 has?

---

