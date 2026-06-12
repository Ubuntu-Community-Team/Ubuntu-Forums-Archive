---
title: "TOSHIBA Satellite A105 fans not working properly"
date: 2013-02-27
forum: Hardware
---

### Post by kunai on 2013-02-27
Hello all,

Recently I dug around in my garage and found my old laptop. Put Ubuntu on it and it's been running great. There is one problem though; the fans don't work properly. I believe this is a common issue with Toshibas under Ubuntu. After a suspend, the fans cease to spin and the CPU overheats, even when performing normal tasks such as browsing the web, resulting in an immediate shutdown with no prior warning signs.

The computer itself runs fine, but this error has been annoying me to no end. The only way I can get the fans to work after a suspend is if I use lm-sensors and keep a terminal around and keep typing "sensors" in, but even that doesn't work. I tried sensors-detect, but it said that no controllable sensor modules were found. 

Another thing, when I do type in "sensors," the readout is

```

acpitz-virtual-0
Adapter: Virtual device
temp1:        +xx.x°C  (crit = +105.0°C)
temp2:         +0.0°C  (crit = +105.0°C)
temp3:         +0.0°C  (crit = +105.0°C)
temp4:        +xx.x°C  (crit = +105.0°C)

```

There aren't any CPU labels or GPU labels there to guide me into knowing which temperature is which. Either way, if I do not monitor sensors frequently, temp1 goes to 74°C and temp4 goes to 65°C. After I run sensors again, the fan immediately kicks in full blast, and then seems to correct itself, and temp1 falls back down to 49-55°C and temp4 usually remains at around 47-48°C. Both of these temperatures are far higher than they should be; I took apart the computer and cleaned out the entire heatsink and fan assembly of all dust and applied fresh thermal paste to the CPU and GPU. Even when my computer was dust-clogged, under Windows XP CPU temps would never go above 60°C at full load, and idle temps used to be around 30-35°C.

So, without lm-sensors working, I'm left with no options. Please help; this computer was very expensive and powerful when I originally bought it in 2005 and still runs like a charm. If the fan problem can be fixed, I can hold out buying a new computer for 2-3 years! :)


Model #: Toshiba Satellite A105
CPU: Intel Pentium M Single-core 1.73 GHz
GPU: Intel Mobile Graphics Chipset
Hard Disk: Seagate Momentus 250GB 2.5" Drive
Memory: Kingston DDR2 800MHz RAM (2 DIMMs)
Motherboard: Toshiba Mobile Motherboard

---

### Post by kunai on 2013-02-27
Bump. :D

---

### Post by kunai on 2013-02-27
Double bump.

---

### Post by mörgæs on 2013-02-28
First of all I would give a Pentium M Lubuntu and not Ubuntu. 

Which release are you using, by the way?

Second, have you upgraded the BIOS?

---

### Post by kunai on 2013-02-28
> **mörgæs said:**
> First of all I would give a Pentium M Lubuntu and not Ubuntu. 

Which release are you using, by the way?

Second, have you **upgraded the BIOS**?

I'm using 12.10 currently. Also, any reason as to why I should use Lubuntu and not Ubuntu? Unity runs fine, performance is smooth and fast, and all Compiz 3D effects are working without the slightest lag.

About the BIOS; unfortunately it can't be upgraded with GNU/Linux, the only upgrade method I found on Toshiba's website is Windows-based and I really don't want to go through the pain of reinstalling Windows, upgrading the BIOS, then switching back to Ubuntu and transferring my files back.

I don't think it's a BIOS issue, however.

---

### Post by JayKay3OOO on 2013-02-28
Most BIOS (F2 or del) at boot have options for fan speed or a cpu config where you can tell the computer how fast you want them to spin. While you are at the bios the fan will spin at an optimal temp where there should be a page with some cpu temps so you can compare how fast it sounds like it's spinning in bios to in ubuntu - that will at least eliminate the bios if you have not done it already.

Does it do this on Windows and have you tried unscrewing the case to get at the fan to check that it's not full of dust or the small metal cooler the exhausts out of the case often gets blocked by dust.

2005, be glad it has lasted this long. Check the hard drive too. If this is getting really hot it could be causing an overheat, but it's most likely the fan is, or the cooler is blocked.

I think my phone has more computing power. Few more years!? Bin it kunai because it's not worth anything now!

---

### Post by kunai on 2013-02-28
> **JayKay3OOO said:**
> Most BIOS (F2 or del) at boot have options for fan speed or a cpu config where you can tell the computer how fast you want them to spin. While you are at the bios the fan will spin at an optimal temp where there should be a page with some cpu temps so you can compare how fast it sounds like it's spinning in bios to in ubuntu - that will at least eliminate the bios if you have not done it already.

**Does it do this on Windows and have you tried unscrewing the case to get at the fan to check that it's not full of dust or the small metal cooler the exhausts out of the case often gets blocked by dust.**

2005, be glad it has lasted this long. Check the hard drive too. If this is getting really hot it could be causing an overheat, but it's most likely the fan is, or the cooler is blocked.

I think my phone has more computing power. Few more years!? Bin it kunai because it's not worth anything now!

There was, I think, a BIOS configuration setting for the processor, but not the fan. There were three settings, I believe; high-performance, low-power, and auto. I had set it to high-performance to get a bit more speed out of it, but I'll try setting it to auto and see if the temps fall a bit.

As for the question you asked (in bold), from the original post:

"Both of these temperatures are far higher than they should be; I took  apart the computer and cleaned out the entire heatsink and fan assembly  of all dust and applied fresh thermal paste to the CPU and GPU. Even  when my computer was dust-clogged, under Windows XP CPU temps would  never go above 60°C at full load, and idle temps used to be around  30-35°C."

As for binning it, I don't really like throwing away perfectly fine hardware. If it works for me, why not? :D

I'll probably have to upgrade to a faster computer soon, though; the geekbench for this one was 1341. I think my friend's Galaxy SIII scored 300 points higher.

---

### Post by kunai on 2013-03-01
Unfortunately, it didn't work. The idle temperatures DID drop by 5 degrees centigrade, but the CPU still overheated after a suspend.

Any suggestions?

---

### Post by mörgæs on 2013-03-01
Yes, the BIOS (still).

At least on Dell you can burn a CD or USB stick with Freedos and boot it. From here you can apply the new BIOS. I don't know if it works on Toshiba.

It surprises me that it runs Unity well, but congratulations. That means you have a computer for many years to come.

---

