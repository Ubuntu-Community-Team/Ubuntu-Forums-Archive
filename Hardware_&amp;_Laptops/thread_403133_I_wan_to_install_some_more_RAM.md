---
title: "I wan to install some more RAM"
date: 2007-04-06
forum: Hardware &amp; Laptops
---

### Post by glaeven on 2007-04-06
so i have used ubuntu for over a year now. i love it. it runs fine on my old machine.

but, because it runs on an old machine, it does run fairly slow. so in an effort to speed it up, i have looked into getting some more RAM.

right now, i have a AMD Athalon Processor (900mHz), and 128 Mb RAM. The video card is old, but is good enough.

my question is simple, if i do get the right type of RAM, will ubuntu detect it, or will i need to re-install? or, is there anything else i need to do?

---

### Post by WW on 2007-04-06
I recently increased the memory in a six year old laptop from 256M to 512M.  If I recall correctly, the first time I turned on the power after adding the memory, the BIOS warned me about the memory change, but I was able to continue, and Ubuntu used the full memory just fine.  I didn't have to do any special in Ubuntu.  I only got the BIOS warning the first time I powered it up; since then, it starts up normally.

---

### Post by mand0 on 2007-04-06
Ubuntu should pick up on your new RAM without any problems.

---

### Post by Valstorm2323 on 2007-04-06
Just be careful that your mobo supports the amount of ram you are getting.
Don't buy a 256 stick of ram if the mobo cannot handle it. I know that my mobo will only accept up to 512 stick of ram in each slot.

Otherwise don't worry. Worst thing that happens is that the computer won't boot and then all you gotta do is remove the memory again. Easy as pie.

---

### Post by Haywood on 2007-04-06
I have a similar issue in that I am currently running 512MB of RAM and just ordered another 512MB.  I am currently have 512MB for a swap file, does this need to adjusted? I know for Windows they recommend 1.5x your actual RAM, does this apply with Ubuntu?

---

### Post by az on 2007-04-06
> **glaeven said:**
> 
my question is simple, if i do get the right type of RAM, will ubuntu detect it, or will i need to re-install? or, is there anything else i need to do?

You will not need to reinstall.  Your motherboard will detect the amount of ram and so will the OS.  Boot into memtest86 (from the grub menu) and test your ram once you have installed it.  That is the only way to test to see if your ram works.

If it is brand new ram, let it run through a few tests (5 minutes).  If you bought it used, let it run overnight.

> **Haywood said:**
> I have a similar issue in that I am currently running 512MB of RAM and just ordered another 512MB.  I am currently have 512MB for a swap file, does this need to adjusted? I know for Windows they recommend 1.5x your actual RAM, does this apply with Ubuntu?

It depends on what you use your computer to do.  It's likely that the best thing for you would be to just leave it alone.  The only time you are *required* to have more swap space than physical ram is when you suspend-to-disk (hibernation).  You need about 25 per cent more swap than ram to suspend to disk (swap).

Look at it this way, when you install the OS (and can't know exactly what everybody's needs are), you will satisfy pretty much everybody's needs by installing a swap that is 2 times the amount of physical ram.  But you have been living with this system with much less ram+swap for this long, so you won't really need it.  Don't worry about it.

---

### Post by Compucore on 2007-04-06
I would agree to what you are saying there and that is usually on the installation phase of Ubuntu or inqindows it creats the swap file 15X larger than your main memory. I don't think you would need to redo everything. It will detect it the new memory in teh BIOS. And Ubuntu will use it as well.  I knew off hand over here when I was doing a installation of a earlier version of Ubunut. I had two drives so places the main programs on one and the accounts on the second drive. During that time when I was creating that. I told Ubuntu to create a swap of 1 gig on both drive. so here was a total of 2 gigs  combined in swapping. But in General after installing ubuntu. You do not have to mess around with recreating your parition. 

> **Haywood said:**
> I have a similar issue in that I am currently running 512MB of RAM and just ordered another 512MB.  I am currently have 512MB for a swap file, does this need to adjusted? I know for Windows they recommend 1.5x your actual RAM, does this apply with Ubuntu?



Compucore

---

