---
title: "4 Gig RAM in Ubuntu?"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by elfstone214 on 2007-06-27
Hi all

I am running 32bit Ubuntu Feisty (2.6.20-16-generic) but I have read that the 2.6.20 kernel supports up to 4 Gig of RAM but Ubuntu is only detecting 3.2 Gig just like in Windows XP. Can anyone tell me what I am doing wrong or missing?

Thanks

---

### Post by bren on 2007-06-27
the rest has been claimed by your graphics card?

just a guess

bren

---

### Post by elfstone214 on 2007-06-27
> **bren said:**
> the rest has been claimed by your graphics card?

just a guess

bren


no I have a dedicated graphics card. it is the issue of the 32 bit OS not recognizing all 4 Gig. But I thought I had read Ubuntu could read up to 4 Gig even if it was the 32 bit version with the 2.6.20 kernel.

---

### Post by arsenic23 on 2007-06-27
If you have a 64bit CPU, boot into a 64bit live CD.  If you see all 4 gigs of RAM there then your problem is that...  well instead of explaining it I'll give you nice linke: -[here]("http://www.interact-sw.co.uk/iangblog/2005/08/05/is3gbenough")-

-------------------------------------------
> But I thought I had read Ubuntu could read up to 4 Gig even if it was the 32 bit version with the 2.6.20 kernel.

I beleive it depends on your hardware.

---

### Post by xzero1 on 2007-06-27
There is an option in my bios that allows an os to use 4 gigs. By default 4 gigs is not allowed. Perhaps your bios has something to do with it.

---

### Post by elfstone214 on 2007-06-27
Ok I think I have figured it out.

I need to either recompile my kernel for my 32bit Ubuntu and there is supposed to be an option for PAE extensions which will alow Ubuntu to read all 4 gig of RAM at the expense of slight CPU resources (3-5%) .... or simply go with AMD64

there you go .... In case anyone else has this question

---

### Post by elfstone214 on 2007-06-27
> **xzero1 said:**
> There is an option in my bios that allows an os to use 4 gigs. By default 4 gigs is not allowed. Perhaps your bios has something to do with it.


my BIOS recognized all 4 Gig by default and I also ran Memtest86+ which also recognized the 4 gig. It is an OS issue as I have found out.

---

### Post by pking on 2007-08-28
Don't know if this will help anyone but I had tons of trouble getting the 32 bit version of Feisty to see all my 4 gigs of ram(forget about the 64 bit edition folks! It can't even recognize my network card!!).

After tons of research here's what worked for me:

1- Default install of Feisty 32 bit desktop edition

2- Blacklisted the "intel_agp" in /dev/modprobe.d/blacklist because I got a PCI express card and otherwise  wouldn't boot.

3- Installed the "server" version of the kernel from Synaptic

4- Reboot

5- Done!

Of course for those who have an Asus P5B-E like me have to enable the "memory remapping" of the north bridge or else you'll only see 3 gigs of ram.

Hope that will help a few.

pking

---

### Post by jaux on 2007-08-28
> **pking said:**
> Don't know if this will help anyone but I had tons of trouble getting the 32 bit version of Feisty to see all my 4 gigs of ram(forget about the 64 bit edition folks! It can't even recognize my network card!!).

After tons of research here's what worked for me:

1- Default install of Feisty 32 bit desktop edition

2- Blacklisted the "intel_agp" in /dev/modprobe.d/blacklist because I got a PCI express card and otherwise  wouldn't boot.

3- Installed the "server" version of the kernel from Synaptic

4- Reboot

5- Done!

Of course for those who have an Asus P5B-E like me have to enable the "memory remapping" of the north bridge or else you'll only see 3 gigs of ram.

Hope that will help a few.

pking

Does your restricted drivers (if you have any) still work? Because I think server kernel doesn't support restricted driver module.

---

### Post by zorkerz on 2007-10-24
I have installed the 64 bit gutsy and it only recognizes 3.8 gigs of ram. While this is close to all and im sure I will no notice any performance issues I would like to know why all 4096 mb of ram are not showing up. Any ideas?

---

