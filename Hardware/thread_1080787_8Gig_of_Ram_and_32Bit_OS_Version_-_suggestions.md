---
title: "8Gig of Ram and 32Bit OS Version - suggestions"
date: 2009-02-25
forum: Hardware
---

### Post by ccranfield on 2009-02-25
Hi Everyone,

I recently got the opportunity to get 8Gig of RAM for my Ubuntu 8.10 box.   I had 4Gig but with the OS and running virutal box (XP) I was always beating up my RAM.

The issue I have is that I am running the 32bit (desktop) version of the OS.   So I need to find a solution to so that I can run the 8Gig of RAM. I was looking at the using a kernel with PAE but I have never built/installed a new kernel myself (I am a newbie).  I also want to be super 'cautious' as I have dual 27" monitors being driven by an ATI card and I am using the ATI FGLXR drivers and I have read that installing a new kernel and kill the drivers?? :(

I would prefer to move the 64 bit - but my virtualbox(XP) is SUPER important to me and I would hate to have to wipe out my entire system to install the 64 bit version.

So what I am looking for is some suggests on the best way I can utilize my 8Gig RAM without having to do a complete rebuilt.  If using the PAE kernel is the way to go could someone point me in the right direction for a FAQ on the best/safest way to do that?

Thanks in advance for any help/suggestions.

C

---

### Post by blazemore on 2009-02-26
You can install the 64 bit version, just back up all your virualbox stuff first.

---

### Post by kidux on 2009-02-26
If your /home is on a seperate partition, then you can install the 64-bit with no problems as long as you don't format that partition when you tell Ubuntu to use it as /home. Your VM's will still be there when you re-install vbox.

---

### Post by Kevbert on 2009-02-26
The 32 bit server version of Ubuntu has PAE built in.

---

### Post by Vince4Amy on 2009-03-01
> I am using the ATI FGLXR drivers and I have read that installing a new kernel and kill the drivers??

Just reinstall the drivers after updating the kernel. I'm not sure about Ubuntu but Fedora and OpenSuSE have a PAE Kernel which you can download from the repositories. If not then install the server kernel or build your own.

---

### Post by 00b00nt00 on 2009-03-01
Surely 8GB RAM + Ubuntu = Overkill!

---

### Post by damis648 on 2009-03-01
32-Bit OS's can natively only support 4Gb RAM total (which includes video memory, that reserved for the kernel, etc.) You have a few options if you need more:
1. You can install the server kernel, it is compiled with PAE which will give you 64Gb RAM support.
2. You can install Ubuntu 64-Bit edition.
3. You can compile your own kernel with PAE, however this sort of thing is a bit over some people's heads.:popcorn:

---

