---
title: "RAM missing after upgrade to 18.04"
date: 2019-03-21
forum: Hardware
---

### Post by liry on 2019-03-21
Hi everyone,

This is my first time posting, so apologies if I don't completely follow etiquette. I've tried the search through the forums to find an answer to my problem but didn't find anything that directly helped. 

My problem is the following. I have inherited a work computer at my university that was running Ubuntu 16. There were 16 GBs (actually 15.6) of RAM and 16 GB set aside for swap. A month or so ago, I accidentally broke my installation and decided to do a clean install of Ubuntu, upgrading to 18. After upgrading, I still have 16 GBs of RAM, but my swap space decreased from 16 GBs to 2 GBs. I'm not sure what happened. I've ignored the problem for about a month because 16gbs was enough for  most of my purposes, but I decided I should try to get this resolved. I am a complete novice when it comes to hardware things, but I tried to follow some of the suggestions of things in the forum, like checking the BIOS and lshw. Here's some of the output from lshw:

     *-memory
          description: System Memory
          physical id: 1
          slot: System board or motherboard
          size: 16GiB

When I check the BIOS, it seems to think there are 4 sticks (slots?) of 4096 MB. 

Other possibly relevant information: it's a 64-bit machine. Here's the output of uname -a:

Linux peregrine 4.15.0-46-generic #49-Ubuntu SMP Wed Feb 6 09:33:07 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Any ideas what I can do or check? On a side note, if I ever find the missing RAM, I would like to keep the size of the swap partition at 2gb and move the rest to memory.

Thanks,
Richard

---

### Post by CatKiller on 2019-03-21
Swap space isn't RAM. It's simply space on the hard drive to put stuff when the RAM is full. With 16 GB of RAM, you aren't going to use swap much at all, and 2 GB is plenty for hibernation. Recent installs don't use a swap partition at all, using a swap file instead.

You don't have anything to worry about. The RAM you have has been detected.

---

### Post by liry on 2019-03-21
Ok thanks for the quick reply. So what you're saying is that I never had 16 gbs of extra memory to begin with on the previous version of Ubuntu. The previous install of Ubuntu I had (it was Ubuntu14.04, but maybe that doesn't make a difference) didn't have a separate swap partition in memory, but a separate swap file on the hard disk, and it was just writing things to hard disk whenever I ran out of RAM. Is that right?

---

### Post by Autodave on 2019-03-21
That is correct.  You are good to go.

---

### Post by liry on 2019-03-22
Great, thanks!

---

