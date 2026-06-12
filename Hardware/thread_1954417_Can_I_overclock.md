---
title: "Can I overclock?"
date: 2012-04-08
forum: Hardware
---

### Post by ZeroCool96 on 2012-04-08
I was wondering if it's possible for me to overclock my CPU.

Here's my specs:

Toshiba Satellite L505D-GS6000
4GB of RAM
AMD Turion II Dual Core Mobile M500 (2.2 GHz)
ATI Mobility Radeon HD 4200

---

### Post by mardicas on 2012-04-08
You should check your BIOS settings weather they enable you to do that. It's not done from an operating system.

---

### Post by jonnyboysmithy on 2012-04-08
A bit of topic but, are the voltages controled by bios or can they also be changed by the OS?

---

### Post by Arielxgbarton on 2012-04-08
My computor, with a AMD processor, has, on the motherboard a knob for adjusting overclocking

---

### Post by mörgæs on 2012-04-08
You are welcome to ask here, but I guess you'll get the best advice regarding hacking your Gibson in a dedicated overclocking forum.

---

### Post by Mark Phelps on 2012-04-09
> **ZeroCool96 said:**
> I was wondering if it's possible for me to overclock my CPU.

Even if you CAN do it, do you want to risk burning up your laptop?

Many laptops already have a problem with overheating with the recent Liunux kernels.  Since you can't add an oversized HSF, and you can't do liquid cooling, driving your CPU even faster, which will make it run even hotter, is asking to burn it out.

---

### Post by Redblade20XX on 2012-04-09
> **Mark Phelps said:**
> Even if you CAN do it, do you want to risk burning up your laptop?

Many laptops already have a problem with overheating with the recent Liunux kernels.  Since you can't add an oversized HSF, and you can't do liquid cooling, driving your CPU even faster, which will make it run even hotter, is asking to burn it out.

I agree with this statement. Technically there is no point to over clock a laptop. Factoring heat production at a "useful" over clock setting and in addition a variable environment, it just isn't worth it.

-Red

---

### Post by HeadlessZombie on 2012-11-13
[CENTER]:---)
[/CENTER]

Yes you can overclock. Radeon GPUs love to be overclocked but the memory not so much.

  Try rovclock or amdoverdivectrl

To install rovclock:
1) Open a terminal window to type command:
sudo apt-get install rovclock

[CENTER]-  =  =  =  -

[/CENTER]
amdoverdrivectrl can be downloaded from:
[http://sourceforge.net/projects/amdovdrvctrl/](http://sourceforge.net/projects/amdovdrvctrl/)

Without any modification; my Mobility Radeon HD 4200 series overclocks 127 MHz without any real heat increase and runs completely stable.

On my laptop that has a desktop Radeon 7500 GPU, I added a very slim heatsink that I salvaged from an old GeForce256 and overclocked the GPU to 496 MHz (Double the original speed.)

---

