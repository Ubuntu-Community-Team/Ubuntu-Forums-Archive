---
title: "Question on 8gb Ram Ubuntu 8.04"
date: 2008-09-19
forum: Hardware
---

### Post by AmbientOcclusion on 2008-09-19
I have 8gb of Patriot pc2-6400 (PDC24G6400ELK) installed and running well with Ubuntu 8.04 64bit.

The ram shows up as 7.8gb does anyone know why this is?

I need the extra ram to run a program called Real Flow and it also works well to have the extra ram with Maya.

I have to install Windows (Vista 64 only license I have) as a dual boot. There are some proprietary programs that do not exist in Linux yet or do not run in Wine that I need. The odd thing that occurs is that I get BSOD's in Vista with the 8gb of ram! My question is why does the ram work well in Ubuntu and cause problems in Vista? I don't get it. I would think that there is a hardware issue that causes OS's to crash...Could someone offer any insight as to why the ram is no problem in Ubuntu and fails in Vista?

The reason I am curious is that if I were not a Linux user, I would have been blaming the hardware as faulty or other standard ram problem issues. So I guess this is really a positive for Ubuntu, but I would still like to know how/why this is...Ultimately I have to get windows to work. 

Would you recommend that I install a vista 64 virtual machine? I suppose with my extra ram it should work well.

Also are there any diagnostic/info programs like siw [http://www.gtopala.com/](http://www.gtopala.com/) for Ubuntu?

Asus P5ne-sli
Intel Core 2 Duo Quad Q6600 2.4ghz
Nvidia GForce 8800 gtx
8gb Patriot pc2-6400 (PDC24G6400ELK) 800mhz

Thanks ahead of time!

---

### Post by AmbientOcclusion on 2008-10-16
The Patriot ram tech support states that Vista and my current Northbridge do not work well together.

---

### Post by Kevbert on 2008-10-16
It may be worth running memtest via the grub menu for a few passes. 7.8Gb sounds about right if your using
```
free -m 
```
to check it.  The rest may be shared or unavailable due to memory hole remapping.
Why the BSODs in Vista? I can't really comment, other than the fact that MS programs/OS are memory hungry.

---

### Post by AmbientOcclusion on 2008-10-16
Cool thanks.

My motherboard oddly enough is missing the BIOS shadow function, I initially thought that would fix it.

```
free -m
```

Indicates I am using 912mb of ram. Which seems odd. System Monitor states I am using 465mb which seems about right. I am wondering if the 912mb figure includes disk cache?

Here is the output:
>              total       used       free     shared    buffers     cached
Mem:          8002        912       7089          0         99        358
-/+ buffers/cache:        455       7547
Swap:        11625          0      11625


---

### Post by mick222 on 2008-10-16
1gig is an approximate figure  so your memory is probably right . The curious thing to me is what is it doing if you only use 912 mb.I can see the point of up to 3 gig if you run vista with aero while playing games but 8 gig.

---

### Post by mick222 on 2008-10-16
just checked out the program your running seems to need a lot of memory some people are using up to 32 gig wow. Sorry but was at the pub earlier,

---

### Post by AmbientOcclusion on 2008-10-17
> **mick222 said:**
> 1gig is an approximate figure  so your memory is probably right . The curious thing to me is what is it doing if you only use 912 mb.I can see the point of up to 3 gig if you run vista with aero while playing games but 8 gig.I use a program called Real Flow and use Maya quite a bit. Also, High Def video editing. Real flow does dynamic particle fluid simulations and can really use any amount of ram and cpu cycle you can throw at it. With Maya I do a great deal of dynamics and mental ray/render man type stuff.

Working with high def renders and large plates is tough. If I could get a mboard with 32 gig capable (and could afford it) I would probably benefit from it...

---

