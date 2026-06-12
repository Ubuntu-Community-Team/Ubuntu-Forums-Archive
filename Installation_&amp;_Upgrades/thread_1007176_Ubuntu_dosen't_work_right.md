---
title: "Ubuntu dosen't work right"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by BobIsLife on 2008-12-10
Hello all.
a few weeks ago i tried to install Ubuntu 8 on my PC. now, i'm a complete Linux newbie and this was my first ever real attempt to get into linux. having said that, i'm a very advanced windows user, and know a lot about hardware (since it was once my occupation). So although i don't know nothing about ubuntu or linux, i can gaurentee that my hardware is working perfectly (although it's a little old) and windows works pretty good (even vista worked fine on this PC).

now, i cleared up 50% of my HD as unpartitioned space (about 160GB) and ran the Ubuntu live CD. i went through the installation and it went smoothly.
afterwards, i started to work with my new ubuntu but something didn't work right. it was very slow, espcialy when surfing via firfox 3. the video card didn't work right at all. evry flash or movie played was distorted and the frames were jumping.
so i've logged to here and searched for issues and\or drivers for my Graphics Card (ATI 9600 256MB - told you it's a bit old) and found some guuides for installation, but none solved my problems.
so i formatted the partition and started over. again - same problem. since i didn't had much time for this, i let that go and returned to windows (sadly). some days ago i tried to log in to ubuntu again, and the installation crashed. after rebooting, i tried to log into windows again, and it worked fine. afterwards i re-partitioned the space for windows use again, but i'm ready to give it another go.
does anyone knows about this problem or how to fix it?

many thanks in advance!

PS - rest of my hardware:
+3200 AMD processor (64 bit)
1GB RAM (400MHz - Kingston)
MSI K8N Neo Platinum Mainboard (nVidia Chipset)
320GB WD Sata2 hard drive

Thanks!

---

### Post by davidbilla on 2008-12-10
Did you try enabling all repositories in Synaptic (System-> Administration-> Synaptic) and installing restricted-drivers (System-> Administration-> Restricted Drivers Manager)?

---

### Post by BobIsLife on 2008-12-10
hi - and thank you for ansewring first of all...

enabling all repositories - did try this, as suggested in one guide i found.
what is the restricted driver manager, and what should i find there?

---

### Post by Igniteflow on 2008-12-10
Go to System-> Administration-> Synaptic as davidbilla said and do a search for 'ubuntu restricted', click the select box and apply changes, this will make playing videos and music a lot easier amongst other things

---

### Post by Igniteflow on 2008-12-10
Go to System-> Administration-> Synaptic as davidbilla said and do a search for 'ubuntu restricted', click the select box and apply changes, this will make playing videos and music a lot easier amongst other things

---

### Post by BobIsLife on 2008-12-10
will try - i'll update this post for any developments...
Thanks!

---

### Post by madverb on 2008-12-10
> MSI K8N Neo Platinum Mainboard (nVidia Chipset)

That could be your problem right there. I was attempting to install a linux server on a machine with that board. I managed to install Ubuntu once but it failed after a while. I got through most of the install of Fedora before it failed.
Windows installed and worked easily on it.

---

### Post by BobIsLife on 2008-12-10
> **madverb said:**
> That could be your problem right there. I was attempting to install a linux server on a machine with that board. I managed to install Ubuntu once but it failed after a while. I got through most of the install of Fedora before it failed.
Windows installed and worked easily on it.
Really!?!
does anyone else knows about this issue or similar issue (maybe regarding &#1502;Vidia chipset)?

---

### Post by madverb on 2008-12-11
I searched for ages and found a few people having the exact same problem but couldn't resolve it. I tried so many things to get it to install but it just didn't want to. I also tried to install FreeBSD, forgot about that one.

You might be lucky and find something but it's not very hopeful. I'd try do some searches on the chipset. I can't remember how thorough my searching was.

---

