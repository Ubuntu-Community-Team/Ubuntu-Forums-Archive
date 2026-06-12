---
title: "3 Gig RAM, only 1 Gig showing"
date: 2011-01-18
forum: Hardware
---

### Post by xtremesupremacy3 on 2011-01-18
Hey there,

I have recently found out that this laptop of mine is actually a 64 bit system and I have been running 32 bit Ubuntu on it all the time since I was unaware of it.
But the oddest thing that I noticed today was that eventhough my laptop (MSI CR700) is equipped with 3G of RAM, only 1G is counted for and 9G for swap.

Can anyone tell me why this is?

I would swap to Ubuntu 64bit but the thing is I have so much installed and it will just take too long to get it all back.

Arthur

---

### Post by gordintoronto on 2011-01-18
When you run Administration/System Monitor, what does it say about your memory?

You won't notice any benefit from 64-bit.

---

### Post by xtremesupremacy3 on 2011-01-18
It says I am using 520MB (69%) of 748.4 MB

and using 97.5MB(1.1%) of 8.8 GiB

And I thought it wouldn't make too much difference using 64bit

---

### Post by rakete on 2011-01-18
Have you run a memory test (from grub menu or live CD) to confirm, that your memory is healthy and not damaged somehow?

My experience with 64bit ubuntu is:
- flash not working
- unknown bugs I couldn't workaround
- 32bit works way better

as long as your are not rendering stuff in 64bit software or using your machine as a server, there is no need for 64bit.

---

### Post by xtremesupremacy3 on 2011-01-18
no i havent, i will run the test and report back

---

### Post by gordintoronto on 2011-01-18
> **rakete said:**
> My experience with 64bit ubuntu is:
- flash not working
- unknown bugs I couldn't workaround
- 32bit works way better

as long as your are not rendering stuff in 64bit software or using your machine as a server, there is no need for 64bit.

Interesting. I've been running 64-bit for a year and a half. Here are the issues I have experienced:
[none]

I view flash files every day. With 10.10, I needed to install a lib to watch DVDs, and I needed a work-around for my webcam, but those were 10.10 issues, not 64-bit.

---

### Post by xtremesupremacy3 on 2011-01-18
Well the original issue seems to have been solved:
It seems that for some reason or another, only 1 GB RAM was used after I last had left my brightness settings down and when I restarted I only had 1 GB, after having restarted after restoring brightness, I have all my RAM back. How odd.

As for 64bit. I only have 3GB RAM, so the 4+ benefit of 64bit system wouldn't really apply to me, and due to the fact that I don't use my laptop for serious number crunching (perhaps some programming every now and then but that's it), I don't see any reason to switch. I might end up with some software I'm used to either not being available or working as well as 32bit, and I'm worried some hardware might not be as well supported.
I think it's a case of the classical saying:
'If it aint broken, don't fix it'

Arthur

---

### Post by cascade9 on 2011-01-19
> **xtremesupremacy3 said:**
> As for 64bit. I only have 3GB RAM, so the 4+ benefit of 64bit system wouldn't really apply to me, and due to the fact that I don't use my laptop for serious number crunching (perhaps some programming every now and then but that's it), I don't see any reason to switch. I might end up with some software I'm used to either not being available or working as well as 32bit, and I'm worried some hardware might not be as well supported.
I think it's a case of the classical saying:
'If it aint broken, don't fix it'

Arthur

Fair enough, but when it comes time to reinstall, 64bit is the way to go. I cant think of anything as far as software goes thats not avaible on 64bit (some programs will pretty much be 32bit forced to 64bit, but they are gettering rarer ever day). 

I've never had a problem with hardware support on 64bit, the only hardware issue I know of for 64bit is some (rare) printers only have 32bit drivers that wont install even if forced to 64bit. 

BTW, you dont need 4GB+ for 64bit to have benefits- 

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

---

