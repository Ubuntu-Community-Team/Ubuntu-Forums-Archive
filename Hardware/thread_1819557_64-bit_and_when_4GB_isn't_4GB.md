---
title: "64-bit and when 4GB isn't 4GB"
date: 2011-08-06
forum: Hardware
---

### Post by x-shaney-x on 2011-08-06
Since 64-bit only comes into it's own with 4GB+ RAM, I am slightly puzzled.

I was thinking of adding a 1GB stick to my laptop, which is currently 3GB.
Thing is, in system monitors and such, my RAM is shown as 2.8GB so presumably, adding an extra GB would show as 3.8-9GB.

Does a 64-bit system still see this as 4GB or not?

---

### Post by .... on 2011-08-06
>  my RAM is shown as 2.8GBIt's probably because of shared video memory, so adding a GB will still give you 3.8GB regardless of 32/64-bit. Even on my 64-bit desktop without integrated video memory, some of my 4 GB is still reserved for hardware addressing and BIOS/ACPI stuff:

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3902       1279       2622          0        194        587
```

---

### Post by x-shaney-x on 2011-08-06
Well I do have intel graphics so that makes sense and I would assume that regardless of hardware, some RAM is going to be reserved so will never be the actual amount.

But the question remains, is it actually making the full use of 64-bit?

---

### Post by akand074 on 2011-08-06
^ yup. I don't have any integrated memory, but it's only showing up as 5.8GB of RAM when I have 6GB. That's because there is always memory reserved. This is normal. 64 bit can read over 4GB (matter of fact it can read up to TBs of RAM).

---

### Post by akand074 on 2011-08-06
> **x-shaney-x said:**
> Well I do have intel graphics so that makes sense and I would assume that regardless of hardware, some RAM is going to be reserved so will never be the actual amount.

But the question remains, is it actually making the full use of 64-bit?

Yes it is (most likely). If you have 4GB of RAM on 32 bit it would probably show about 3.2GB I believe. Though, not in Linux anymore as their 32bit PAE kernel can read up to 64GB of RAM I believe. I wouldn't worry yourself over it too much.

---

### Post by .... on 2011-08-06
> **x-shaney-x said:**
> But the question remains, is it actually making the full use of 64-bit?
This question doesn't make sense. If you have a 64-bit system in place, there are very few reasons to install a 32-bit one for the sake of switching.

---

### Post by DeceptiveHornet on 2011-08-06
I had a similar issue in Windows 7. Running 32bit it only registered 3.4 or 3.6gb ram when i have 4GB. Installing 64bit made all 4GB available. Also, as others already mentioned, shared memory with GPU can cause some unexplained loss in RAM space available.

---

### Post by x-shaney-x on 2011-08-06
> **.... said:**
> This question doesn't make sense. If you have a 64-bit system in place, there are very few reasons to install a 32-bit one for the sake of switching.

Well I wasn't talking about switching systems.

I have a 3GB laptop which has 64-bit windows 7 installed.
I also have various linux distros installed, one is 32-bit, the others 64-bit.

It is my understanding, 64-bit dramatically improves performance with certain tasks but only with 4GB+
So the question is all about what a 64-bit systems SEES as 4GB.

I have never really read up on 64-bit much but bits and bobs I have read suggest that most linux programs don't actually make use of it anyway but I don't know how much is true since I just find conflicting information everywhere.

---

### Post by walt.smith1960 on 2011-08-06
I'm under the impression that even with < 4 GB, 64 bit has some memory management  advantage over 32 bit.  I don't think there's much downside to 64 bit in Linux and there seem to be advantages especially with demanding  apps like video editing.  MS Windows that may not be true; there are a fair number of apps that specify 32 bit only.

---

### Post by akand074 on 2011-08-06
> **walt.smith1960 said:**
> I'm under the impression that even with < 4 GB, 64 bit has some memory management  advantage over 32 bit.  I don't think there's much downside to 64 bit in Linux and there seem to be advantages especially with demanding  apps like video editing.  MS Windows that may not be true; there are a fair number of apps that specify 32 bit only.

All true. 64 bit is **significantly** more efficient in handling memory, regardless of how much you have. Thing is, most applications aren't very memory intensive anyways (or already run really fast) that the difference isn't necessarily visible. But overall performance should be noticeably better. More memory intensive applications should perform much better as well. 

Right now there is no disadvantage to 64 bit (in Linux anyways). I've used 64 bit since my first Ubuntu setup back in version 8.10 without issues but it's even better now. Ubuntu installs 32 bit libraries as well so basically if there is applications that only run in 32 bit, they will still install and run fine.

Basically, keep a 64 bit install. Don't worry so much about how much memory you have, like I've said, 64 bit supports a **huge** amount of RAM, if you are noticing less than what you expect, it's likely because memory is being reserved for other things.

---

### Post by .... on 2011-08-06
> **x-shaney-x said:**
> It is my understanding, 64-bit dramatically improves performance with certain tasks but only with 4GB
Okay, now I understand your question. You can encode a video on a 64-bit OS with 2GB of RAM, and it will still be faster than a 32-bit one on the same 2GB system (unless you're running out of RAM).

So you only benefit from another GB of RAM if you're usage requires it, and 32/64-bit is irrelevant (assuming you're using PAE-enabled kernel with 32-bit).

---

### Post by x-shaney-x on 2011-08-06
Now you mention it, I rarely see my RAM usage go above 1GB and the only times it does is when doing extensive image or video editing and such and even then the highest I ever saw was 2.2GB (though I don't obsessively check anyway).

So in my case the questions seems pointless really.
I see very little difference between using a 64-bit OS compared to a 32-bit one.
Some things do run a little smoother but then I have noticed that even when idle the 64-bit versions use more memory so obviously it is reserving more memory so things happen quicker because it isn't having to allocate it on the fly?

---

### Post by DeceptiveHornet on 2011-08-06
Perhaps it's worth also pointing out that 64bit helps you take advantage of the full CPU functionality such as dual / quadrouple cores. This might be primarily intersting if you use the computer for film editing, music projects etc.

---

