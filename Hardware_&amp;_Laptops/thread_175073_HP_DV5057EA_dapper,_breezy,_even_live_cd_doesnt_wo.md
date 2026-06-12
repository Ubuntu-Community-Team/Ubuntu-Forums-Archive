---
title: "HP DV5057EA: dapper, breezy, even live cd doesnt work"
date: 2006-05-12
forum: Hardware &amp; Laptops
---

### Post by medy on 2006-05-12
Hello!

I just bought a new laptop - HP Pavilion DV5057EA ([http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c00604701&jumpid=reg_R1002_USEN](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c00604701&jumpid=reg_R1002_USEN))

Basic hardware info:
AMD 64 Turion ML-32
1 Gb RAM
ATI Radeon Xpress 200M

Problem: installation stops really quickly and says:
**Kernel panic - not syncing: Attempted to kill init!**
(Dapper 6.06 beta or Dapper 6.06 daily build for amd64, even live CD Breezy amd64)

I tested my RAM with live ubuntu CD and it passed ok several times. I really dont know where the problem would be. I have been ubuntu users for 2 years now on my desktop computer but I have no experience with laptops and 64 bit technology. 

I also tried Gentoo - same problem, But knoppix live CD from 2005 worked ok and booted my machine. 

Maybe picture would help someone to see what could be wrong.

---

### Post by medy on 2006-05-13
I also tried Gentoo minimal CD for AMD 64 and got a blank screen. Then I tried Debian testing net install CD and I also got blank screen (with laptop running, but no visual activity)

This hardware works good under windows. So it cannot be a hardware who would cause kernel panic. Memtest reports no memory errors. What is strange that I googled some simililar HP models of laptops with allmost the same hardware and they didnt have problems. 

Only difference that I spoted was that I have AMD ML-32 processor and they had ML-44 processor. 

Next step Im going to use is to stop using rewritable CDs and try to burn on normal ones with minimal burning help. Think that may help? 

I susspect that there could be ATI graphic card who is causing the problem. Is there a boot option of workaround or something?

All suggestions are appreciated.

---

### Post by n3tfury on 2006-05-14
i'm a little confused.  are you saying you cannot install from a normal installation iso or you cannot boot or install from a live cd?

---

### Post by medy on 2006-05-14
Actually both. Install CD didnt work nad also live CD didnt work. They both gave kernel panic. 

But i found a solution though: Debian testing net install (with special boot option) went through :) I think that it must my hardware who is causing the problem. Or default kernel on install cd and live cd doesnt support my laptop.
So, I guess I will have to stick to Debian. Right now Im using kernel 2.6.15-1-amd64-generic and it works fine. It even recognized my ATI graphic card on default :)

The only problem that I have right now is how to build Debian the way I like it. With ubuntu I had  many beatifull tutorials to follow, but with Debian I dont know. Is it possible to use Ubuntu guide like [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu) to help myself see which files I need to download?

---

### Post by sciyoshi on 2006-05-19
What was that boot option? Did you try using it at the Ubuntu boot screen? Also, you might want to look around in your BIOS for stuff...

---

### Post by medy on 2006-05-20
Ok, boot options with breezy were: boot vga=771 noapic nolapic. The installation went ok, but X screen doesn't work at all. Not just graphichal, even console screen doesn't.

As with dapper, i allways get the kernel panic error.  I tried several boot options but allways same result. 

I looked over the forums and others people have simililar problems. One distro work, other not. For me in Knoppix and Debian worked. It must me the kernel-hardware issue. Debian unstable netinstall is using kernel: 2.6.15-1-amd64-generic and its fine. 

If anyone has an idea how to help me to run ubuntu, feel free to post. Im used to ubuntu, but if I will have to stick to debian, i will.

I dont know, should i bust a bug for dapper on this issue? To sum up: I have A specific hardware and ubuntu doesnt work on it at the moment with its normal seetings. If aynone has idea how to modify it to work as Debian does, I will be glad. My computer is notebook HP Pavilion 64 Turion with Ati xpress 200

Best
Matej

---

