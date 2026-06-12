---
title: "I want my 1GB RAM!"
date: 2009-09-19
forum: Hardware
---

### Post by carlosgs91 on 2009-09-19
.

---

### Post by earthpigg on 2009-09-19
you need to use 64-bit ubuntu and windows, not 32.

---

### Post by mimat on 2009-09-19
No hp did not lie to u they did give u 4 gigs of ram but 32 bit os (windows vista and ubuntu) in your case doesnt use all 4 so u have to install 64bit ubuntu just find it on der website and then it should use all 4 gigs of your ram:P:popcorn:

---

### Post by carlosgs91 on 2009-09-19
.

---

### Post by cbope on 2009-09-21
The short answer: Unless you actually NEED that 4GB of RAM, then I would stick with a 32 bit OS for now. Very few apps need or will use more than a gig (or two) of RAM at a time. 

The long answer: The limit for 32-bit apps is 2GB, per app/process. On a 32-bit OS, the actual amount of memory that can be addressed is 4GB, but you have to subtract all memory addressable devices such as your video card's framebuffer memory, plus some reserved memory addresses, from that 4GB. After deducting all of this memory, you are left with approximately 3GB on most systems. That is the amount of memory available to your 32-bit OS.

On a 64-bit OS, the system can address all of your available memory and is not limited to 2GB per app. So unless you actually have an app that needs more than 2GB, there is little if any benefit to going 64-bit. A 64-bit OS is not inherently faster than a 32-bit one, it just has access to more addressable memory. Unless you need a specific 64-bit app or more than ~3GB of usable memory, 64-bit is not necessary. Also with a 64-bit OS, you run the risk of an app or driver not being available or does not work in a 64-bit OS. On the Windows side, all drivers must be 64-bit, 32-bit drivers are not compatible.

As a previous poster already mentioned, you are not being screwed by HP, they gave you 4GB of RAM. But they did give you a 32-bit OS which cannot use all of that RAM. Just don't jump to 64-bits without understanding what it really means, from a driver and application compatibility point-of-view.

---

### Post by carlosgs91 on 2009-09-21
.

---

### Post by earthpigg on 2009-09-21
> does Ubuntu provide any tool to read 32 bits programs on a 64 bits processor?

you can force install a 32-bit app if running 64-bit ubuntu, or you can repackage a 32-bit .deb to be 64-bits.

everything that is open source in the ubuntu repos is avialable in both 32 and 64 bits.

what do you think you will need to install that is 32 bits only?

---

### Post by lykwydchykyn on 2009-09-21
The optimum solution is to move to 64 bit Linux,  but you can get the full 4 GB in 32 bit mode by installing the server kernel.  Whether or not it will actually improve your computing experience is something you'll have to determine.

---

### Post by carlosgs91 on 2009-09-21
.

---

### Post by earthpigg on 2009-09-21
> I dont know, maybe the wi-fi driver. Anyway, most of the programs are now in 32 and 64 bits, aren't they?

yeah. i use 64 bit on everything except my (32 bit only) netbook and have no issues.

> P.S.: Can't I pass from 32 bits to 64 directly in Ubuntu without deleting all my content and installing it again?


no, but you can back up and then restore your /home folder after the reinstall to keep personal data and program settings.

---

### Post by lykwydchykyn on 2009-09-21
> **carlosgs91 said:**
> 

What's the server kernel? How do I install it?



It's a kernel compiled with different options that are more suited to server use than desktop use; notably in this case, physical address extension (PAE), which enables you to use up to 64 GB of RAM in a 32 bit environment.

Just open your package manager and install the package "linux-server".  Then reboot and select the server kernel during boot-up (it'll probably end up as the default, actually).

---

### Post by carlosgs91 on 2009-09-24
.

---

### Post by cbope on 2009-09-26
If you buy a retail version of Windows 7, the product key supplied is valid for both 32 and 64-bit versions. You will only get one installation media though, 32 or 64-bit. MS will ship you a 64-bit media for a nominal charge if you have bought the 32-bit version and want to go 64-bit. Since you have a valid product key if you buy the retail 32-bit version, just use the same key for 64-bit.

However, if you buy the cheaper OEM version of Windows, you are stuck with 32 or 64-bit, they will not sell you a 64-bit media, nor will your OEM 32-bit product key work in 64-bit. This is one of the limitations of the OEM version. You are also not allowed to transfer the license to another PC with the OEM version. Retail versions do not have these limitations.

> **carlosgs91 said:**
> Thanks for the reply, anyway most of the programs are available for 64 bits, and there're not much drivers that I need to install (at least in Ubuntu). Maybe I'll install Ubuntu 64bits edition in a 5Gb partition just to try it.

The problem will be Windows. I have Windows 7 for only €29 and I don't know what I'm going to buy, I think that it will be better to buy the 32 bit version of Windows 7 and if I need the 64 bits version or I want to try it I'll have to crack it because I don't think Windows will give me the 32 and 64 bits versions for free.

P.S.: I read that Windows (at least Vista) allows you to open 32 bits programs under 64 bits using a tool called WOW64 (Windows on Windows), does Ubuntu provide any tool to read 32 bits programs on a 64 bits processor?

---

