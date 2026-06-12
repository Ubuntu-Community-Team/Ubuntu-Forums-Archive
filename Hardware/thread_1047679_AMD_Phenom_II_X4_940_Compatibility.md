---
title: "AMD Phenom II X4 940 Compatibility?"
date: 2009-01-22
forum: Hardware
---

### Post by dtsmith1984 on 2009-01-22
My home computer recently died.  I've been looking around for new hardware, and have come across a combo deal at newegg that seems to be a good deal.  My only worry is with it's compatibility with Ubuntu.  I tend to keep up with the latest versions.  

The Hardware:
CPU - AMD Phenom II X4 940 Denab 3.0Ghz Socket AM2+
MOBO - Biostar TForce TA790GX A2+

[Link For Details]("http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.153681")

And I was planning to throw in 4GB (2x2) Kingston HyperX DDR2 1066 Ram.


Has anyone tested any of this hardware with Ubuntu, or even maybe the chipsets?

I really would like to avoid getting hardware that will cause me lots of issues since this computer will be a Ubuntu only computer.

Thanks in advance.

---

### Post by cb951303 on 2009-01-22
CPUs and MOBOs work in a standard way. I wouldn't worry about compatibility. But be careful with integrated devices on your MOBO such as audio and ethernet. They may not be compatible as they require specialized drivers. That being said, the audio and ethernet chip on this mobo is exactly the same with mine so I can say they are compatible. Be careful with the integrated ATI though, messy support.

---

### Post by dtsmith1984 on 2009-01-22
The Video card I had before was ATI Radeon X1650 512mb PCIe. Would the integrated HD3300 be worse to configure?  I've had lots of problems in teh past with my X1650 so I'm pretty much used to installing the ATI Drivers from their website.  So I'm not too worried bout that.

But I've never dealt with ATI Integrated graphics.  Is it different in any way?

---

### Post by cb951303 on 2009-01-22
> **dtsmith1984 said:**
> The Video card I had before was ATI Radeon X1650 512mb PCIe. Would the integrated HD3300 be worse to configure?  I've had lots of problems in teh past with my X1650 so I'm pretty much used to installing the ATI Drivers from their website.  So I'm not too worried bout that.

But I've never dealt with ATI Integrated graphics.  Is it different in any way?

I don't think it's any different, I was just referring to bad ati experience on forums. Officially it's supported. If you're used to configure ATI card then by all means go with that mobo.

---

### Post by thepizzaman on 2009-01-22
man that is a good deal................ can you get me one? jk lol..... i would love to know how well this processor does

---

### Post by cb951303 on 2009-01-23
> **thepizzaman said:**
> man that is a good deal................ can you get me one? jk lol..... i would love to know how well this processor does

from what I've read:

any other intel cpu < Phenom II 940 < Intel i7 --- performance wise

---

### Post by jalfthan on 2009-03-06
All,

Asrock **A780FULLHD** -motherboard
AMD **HDZ940XCGIBOX** Phenom II X4 3Ghz AM2+ 8Mb -processor
Kingston **KHX8500AD2/2G** 2GB 1066Mhz non-ecc cl7 Dimm x 4 (4x4GB also possible with this mobo) -memory

Just works :)

---

### Post by kpatz on 2009-03-06
I have a Phenom II X4 920 in my new server build, works great.  The 940 is just a faster version.  I'm running with an ASRock A780GXE/128M mobo.  Running Intrepid 64-bit Server Edition.

I was able to get the CPU speeds to adjust based on load, and lm-sensors can show the CPU temperature, but not for all 4 cores individually (no matching driver).

Video works fine, though I haven't messed around with ATI drivers to get accelerated video, yet.  It's on my to-do list but not a high priority.

---

### Post by linuxisevolution on 2009-03-06
> **dtsmith1984 said:**
> My home computer recently died.  I've been looking around for new hardware, and have come across a combo deal at newegg that seems to be a good deal.  My only worry is with it's compatibility with Ubuntu.  I tend to keep up with the latest versions.  

The Hardware:
CPU - AMD Phenom II X4 940 Denab 3.0Ghz Socket AM2+
MOBO - Biostar TForce TA790GX A2+

[Link For Details]("http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.153681")

And I was planning to throw in 4GB (2x2) Kingston HyperX DDR2 1066 Ram.


Has anyone tested any of this hardware with Ubuntu, or even maybe the chipsets?

I really would like to avoid getting hardware that will cause me lots of issues since this computer will be a Ubuntu only computer.

Thanks in advance.

I hope you bought it because the link says "This combo deal is not longer available." Although the only thing I ever had to worry about is your video being supported. Cpu's, motherboards, and chipsets are pretty standard now adays. Integrated audio and ethernet has always worked for me on all Linux distros since 6.10, so don't worry there unless it's based on ATI. My motherboard's SLI is even supported :P I think the 32gb ram would be supported to lol. :D

---

