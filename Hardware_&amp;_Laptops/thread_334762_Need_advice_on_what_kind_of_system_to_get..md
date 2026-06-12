---
title: "Need advice on what kind of system to get."
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by CJNyfalt on 2007-01-09
Hi,

I'm planning to get new central computer parts (box, power supply, motherboard, graphics card, memory and processor). I'm totally out on the latest hardware, but here are my needs:
- Dual boot Linux & Windows XP.
- Windows will be used for gaming, World of Warcraft mainly.
- Linux for development and internet use.
- I'm not worried about cost, but I refuse to pay extra for power I don't use.
- 3Ghz processor and 1 GB memory should be enough for me.

What I need advice on are:
- Processor types: Cores, AMD vs Intel, 32 vs 64-bit.
- Motherboard type.
- Graphics card, functionality is more important than politics.
- Memory type.
- Powersupply effect.

---

### Post by kebes on 2007-01-09
A good place to start is the Ubuntu hardware support list:
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

-Processor: You may aswell go 64-bit, since it's "the wave of the future" and not really any more expensive right now. I would also recommend dual-core. From what I've seen, AMD chip+nForce 500-series motherboards have excellent performance and are well supported in Linux. (Do a specific search before buying a particular model, but generally they work without hassle.) The core2duo chips are currently very good performance per dollar. However there are some growing pains in terms of Linux support (for example 965 chipset boards don't work, [see here]("https://wiki.ubuntu.com/Core_2_Duo_Support")).

-Motherboard: I've had good experiences with ASUS, but the more important thing is to make sure the chipset is well supported with Linux. (Like I said, nForce 500-series seem good. nForce 600 might be too new. Similarly the Intel 965 has issues with Linux kernels 2.6.17 and older, which includes Edgy.)

-Graphics: For a modern high-performance card, I would say nVidia. The nVidia proprietary driver is stable and works great. (The only reason to not use it would be ideological reasons.)

---

### Post by CJNyfalt on 2007-01-10
Thanks for the reply!

> **kebes said:**
> 

-Processor: You may aswell go 64-bit, since it's "the wave of the future" and not really any more expensive right now. I would also recommend dual-core. From what I've seen, AMD chip+nForce 500-series motherboards have excellent performance and are well supported in Linux. (Do a specific search before buying a particular model, but generally they work without hassle.) The core2duo chips are currently very good performance per dollar. However there are some growing pains in terms of Linux support (for example 965 chipset boards don't work, [see here]("https://wiki.ubuntu.com/Core_2_Duo_Support")).



What about 64-bit processor and Windows? Can I run XP and normal windows applications on one?
What about Linux? Flash is AFAIK not working on 64-bit machines.

---

### Post by robenroute on 2007-01-10
Windows XP (32-bit flavour) works fine on 64-bit systems, so does Linux 32-bit. There are issues with 64-bit support concerning software tools/utilities, although I haven't checked lately, so issues could have been resolved in the last few months.

If you want to be safe for the time being, just use 32-bit software/OS versions.

Like Kebes mentioned, stay away from the Intel 965-based boards. Have a look at [Phoronix]("http://www.phoronix.com"). They regularly test motherboards, graphics cards, PSUs, and all other kinds of hardware. Read a few motherboard reviews available on their website. The best "Linux" board they've recently come across is the Abit KN9 Ultra (nForce 570 Ultra-based); just about everything on that board is supported in Linux.

People also have reported good experiences with MSI's K9N Platinum and Diamond boards.

Let us know how you go! Thanks.

---

### Post by CJNyfalt on 2007-01-12
Thank you! I'll try to remember to report.

---

### Post by arsenic23 on 2007-01-12
When it comes to processors I think at the moment everyone should be recomending Core 2 Duos (Intel).  I consider myself an AMD fanboy, ( haven't owned an Intel CPU since my old 133 ), but the Core 2s are just hands down the best bang for your buck at this moment.

Here's a good interactive CPU chart to prove my point: [http://www23.tomshardware.com/cpu.html](http://www23.tomshardware.com/cpu.html)

While I'm at it here's the same style charts for graphics cards: [http://www23.tomshardware.com/graphics.html](http://www23.tomshardware.com/graphics.html)
As always I recomend Nvidia, not because they make better hardware, but because they make better drivers.  ( I can't say that this is fact, but it's a widely held opinion. )  And of course Nvidia makes their own linux drivers so they always seem to run better outside of windows for me.

Now asuming you choose to get an Nvidia card you'll more then likely want at least a 6600GT to run WoW.  I particularly like the 7800s and 7900s, and they will simply destroy WoW.  

Now here's something interesting you might want to consider for a boot setup.  In order to not have to mess around with boot loaders and whatnot when it comes to to reformat or mess with my windows partitian I personally run an odd setup that you may want to consider.  

I have two relatively small drivers set up as a striped raid and running XP.
I then have a 400gig external eSATA which I have Ubuntu installed on.  If your unfamiliar with eSATA, it's basically a SATA extention cable that lets you house a drive outside your main machine while still getting the transfer speeds of SATA.  
The raid is on sda2 and sda3, the external linux drive is on sda0.  By doing this I can dual boot without actually dual booting.  If I want to boot into linux, I turn the external drive on and then the PC.  If I want windows I just turn the machine on.  If I need to access my ext3 particians I can just turn on the linux drive and windows will detect it on the fly with little trouble.  I can then use the IFS tools to mount the ext3 setup in windows.  But I think you get the idea.

I only mention this because I find playing WoW without a split raid is alot like getting your teeth pulled.

Well, I hope that bit of before bed rambling was helpfull.  Just remember, you should take any advice you get with a grain of salt, including my own.

---

### Post by robenroute on 2007-01-14
Interesting set-up arsenic23. Could you spoil us with a wee bit more on the tech specs of your system? Motherboard, CPU, memory, etc.

Thanks in advance!

---

