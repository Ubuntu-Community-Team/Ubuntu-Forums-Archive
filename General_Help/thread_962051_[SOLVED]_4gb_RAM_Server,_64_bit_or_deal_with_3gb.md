---
title: "[SOLVED] 4gb RAM: Server, 64 bit or deal with 3gb?"
date: 2008-10-28
forum: General Help
---

### Post by Crusty Juggler on 2008-10-28
I just got a new laptop that came with 4gb ram and I'm waiting for Intrepid to come out so I can stop using Vista.  

After reading up a bit on the 4 gig issue, it seems that my best choices are to install the server version, install the 64 bit version or just install the 32 bit and deal with it only recognising ~3gb.  

I'm not quite adventurous enough to recompile and enable PAE support, plus I want to get this laptop running Ubuntu so I can start using it for every day purposes. 

Of these three options, installing the 64 bit version seems to be the most favourable, but I just want to make sure that 1) running 64 bit Intrepid on a 32 bit system is okay; and 2) that running 64 bit Intrepid won't cause grief later on down the road with software compatability.

Thanks!

---

### Post by drelyn86 on 2008-10-28
> **Crusty Juggler said:**
>  I want to get this laptop running Ubuntu so I can start using it for every day purposes. 

What every day purposes require more than 3 gigs of ram?

---

### Post by tuxxy on 2008-10-28
I would go for the 64-bit that way you get to access all your RAM and have the benefit of 64-bit OS too :)

> **drelyn86 said:**
> What every day purposes require more than 3 gigs of ram?

Video/Photo editing, virtualisation etc

---

### Post by LowSky on 2008-10-28
> **drelyn86 said:**
> What every day purposes require more than 3 gigs of ram?

Have you tried to use Vista?
LOL

Seriously go 64Bit, there is no issues using 64bit these days.  Within a year everyone will need it when 8GB of RAM is the new norm.

---

### Post by TeXtonyx on 2008-10-28
If your computer came with 4GB it may be able to run a 64-bit OS,
but you should check that your motherboard is 64-bit capable. It's
not a default having hardware that supports a 64-bit OS. Find out
the model of your mainboard and google it with 64-bit capable. Or
your documentation might tell you. Yes, they do sell 4GB of ram
on systems that can't utilize it (only 32-bit hardware). Also one
has to check that your peripherals have 64-bit drivers available.

Yes, if your laptop runs 64-bit Vista you are safe. But they never
come that way unless you order it. Now, the default is always 32-bit.

---

### Post by tuxxy on 2008-10-28
If your already running Vista 64-bit theres your answer, although they do come with 32-bit still a lot of the time.

---

### Post by sdennie on 2008-10-28
I would install the 64bit version.  However, if you are nervous about going 64bit, you can just install the 32-bit server kernel (it's trivial).  Unless you are playing games, you probably won't notice a difference in performance between the server and generic kernels.  It sounds like you may have already read this but, I'll link it anyway: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

---

### Post by Crusty Juggler on 2008-10-28
Thanks for the quick replies.

This is a 32 bit system (C2D P8400 cpu) with 32 bit Vista and yet, strangely, 4 gb ram. 

As to the question what do you need 4 gb for, I don't.  But this computer has everything I wanted, in addition to a ridiculous amount of ram.  And since it's there, I might as well use it!

Sounds like the 64 bit version is the way to go.

Also- the laptop in question is a Toshiba Satellite A300/c01, which appears to ship with Vista 32 bit but with recovery discs for 64 bit.  Confusing.

---

### Post by TeXtonyx on 2008-10-28
OP wrote: Sounds like the 64 bit version is the way to go.

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/1006661.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/1006661.html)

It sounds likely that you have a license for Vista 32 and 64 bit.
That means that the hardware/mobo will be up to snuff for 64-bit.

The worst that can happen is that you download the Ubuntu 64-bit
version, burn it, and it fails to install because your hardware 
doesn't meet the 64-bit criteria. If Ubuntu doesn't come with the
drivers for the laptop and peripherals, you'll find some of them
at the manufacturer website. However, if the drivers work too 
poorly, 1GB of ram won't make up for it. I've read that 8.10 has
better support for the newer video drivers, but its awfully new.

---

### Post by DGortze380 on 2008-10-28
> **Crusty Juggler said:**
> Thanks for the quick replies.

This is a 32 bit system (C2D P8400 cpu)

If it's a Core 2 Duo, it's a 64bit CPU, not 32bit CPU.
Just because it comes with 32bit Vista doesn't make it a 32bit system. You can run 32bit on a 64bit processor, but not 64bit on a 32bit processor.

Suggestion for original question: install 64bit Ubuntu.

---

### Post by Crusty Juggler on 2008-10-28
64 bit it is, then.  Thanks again, everyone.

---

### Post by aurelieng on 2008-10-29
> **Crusty Juggler said:**
> 
I'm not quite adventurous enough to recompile and enable PAE support, plus I want to get this laptop running Ubuntu so I can start using it for every day purposes.

AFAIK, PAE is enabled by default in the server kernel. Nothing to recompile, nothing adventurous :)

---

