---
title: "suggestions on custom built PCs"
date: 2012-11-03
forum: Hardware
---

### Post by mzrk7 on 2012-11-03
Hello everyone!
I'm going to change my pc and I would like to have some advice in custom building of Pcs. Last time I built a Pc processors and video cards were separated. Now things are not that easy to tell. I would like to know how good is the state of linux support for a pc with an apu and a dedicated videocard. 
Can you help me out? Thank you! :D

---

### Post by ahallubuntu on 2012-11-03
What is your goal with this PC?  What do you want to do with it?  It's possible to build a cheap, basic PC that performs well but won't do well with games - or one that will be top-of-the-line and cost a lot more.

CPUs still aren't built into the motherboard except in rare cases like the Intel Atom (a netbook CPU sometimes used in low-power/low-cost desktop motherboards).

Many motherboards now have integrated video, but if you do any gaming, you may wish to make sure the motherboard has at least one PCI-E X16 slot so you can add a better graphics card.

Support in Ubuntu's version of the Linux kernel tends to lag new hardware a bit.  So the very newest chipsets may not automatically be supported.  If you buy something a year old, it will be much more likely to work automatically.  Again, I don't know what your goal is.  Personally, I prefer older technology that's cheaper - and more likely to have good support - instead of the newest, fastest hardware that may not be well supported yet.  

What about power consumption?  This is something I care about more than performance these days.  Some CPUs are more power-efficient than others.  Check the specs.  A CPU that has a spec of 35W TDP (maximum power the CPU package is spec'ed to tolerate) will consume less power than one that is rated at 95W TDP.

If you care about power consumption at all and your PC will be on very long every day, get an efficient,  80+ rated power supply.  You may save 10+ watts just because of the efficiency.  If this PC will be used for years, the efficient power supply will eventually pay for itself, and they don't cost that much these days anymore, anyway.

---

### Post by mzrk7 on 2012-11-03
I was thinking about a general purpose pc, good at all around tasks, so that I can do my everyday workings and some casual gaming now and then. The thing that puzzles me is that many of the new CPUs have built in GPUs. And I don't know how good is the linux support for a system that has such a GPU, plus a dedicated video card.

---

### Post by CalcProgrammer1 on 2012-11-03
I built a fileserver/TV PC earlier this summer with an AMD Llano A8-3870K APU.  This is a quad-core 3.0GHz processor with AMD RadeonHD 6550 GPU in one chip.  I find it works very well for my needs, it handles light gaming well (as much light gaming as Linux can take anyways, want to run Steam on it when it comes out for Linux as Wine is having issues).  If you want more power, you can use a traditional CPU from AMD or Intel and a discrete graphics card (AMD or nVidia).  I would not recommend Intel's CPU+GPU solutions for gaming, as Intel's GPU's are incredibly weak compared to AMD's and nVidia's offerings.  That said, AMD's APU's combine a nice quad-core CPU with a reasonably powerful discrete-class GPU in one affordable, low power, easy to install package which is great for general purpose/light gaming machines.

Edit:
You can also use an APU (or Intel's CPU+GPU offerings) with a discrete GPU card.  In most cases, you will select what GPU you want in the BIOS (by setting either onboard, PCI, PCIeX, etc).  If you use AMD you might be able to choose a supported GPU for hybrid CrossFireX, which uses both the integrated GPU and discrete GPU together for more performance.  For this, you must use the proprietary Catalyst drivers as the open source drivers do not support multiple GPU operation.

---

### Post by mzrk7 on 2012-11-04
would crossfirex work with an integrated ati on the cpu plus a discrete nvidia, or would it work only with 2 ati cards?

---

### Post by Yellow Pasque on 2012-11-04
> I would like to know how good is the state of linux support for a pc with an apu and a dedicated videocard.
If you have a system with an APU (CPU+integrated GPU), and you add a discrete card, the BIOS will disable the integrated graphics and Linux won't detect it. In other words, it will work just like the non-APU systems you're familiar with.

> would crossfirex work with an integrated ati on the cpu plus a discrete nvidia, or would it work only with 2 ati cards?
Crossfire only works with ATI cards and is a bad idea on Linux (and even on Windows, unless you need two high-powered cards).

> I was thinking about a general purpose pc, good at all around tasks, so that I can do my everyday workings and some casual gaming now and then.
If I had to build such a system, my personal preference would currently be Intel (and all of the systems I've built for personal use over the last 7 years have been AMD). This CPU is pretty popular and is what I would use if I wanted a fast CPU: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819116504](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116504)
The advantage of using Intel is the integrated graphics. They are not the fastest, but may be perfectly suitable for light/casual gaming (and they accelerate video playback).

If you find the Intel graphics insufficient, you can always add a card later. Avoid ATI/AMD and use Nvidia GeForce GTX 550/650 for a good midrange gaming card.

---

### Post by mzrk7 on 2012-11-09
Thank you very much! The best suggestions I could hope for! :D

---

