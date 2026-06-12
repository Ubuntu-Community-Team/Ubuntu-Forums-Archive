---
title: "How well does (K)(X)Ubuntu 7.04 work with this notebook?"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by mastercoderx on 2007-08-06
Hi everyone

I'm planning on buying a notebook computer, which I plan to install (K)(X)Ubuntu 7.04 on.

I'm living in Australia.

I want a fully Linux-compatible notebook (or as linux compatible as possible).


I'm thinking of buying an Acer Aspire 4310-300508 [.]("http://global.acer.com/products/notebook/as4310.htm") notebook.

I want to know how compatible is this notebook with Linux.


The website says this notebook has Intel® GMA 950 graphics, so 3d acceleration should work good.




These are the notebook's specs:

Dolby Digital Sound

Intel Celeron M  1.6 GHz processor

512 MB RAM

14.1" wide LCD monitor

80 GB HDD

(note: these specs aren't from the website, they're from a magazine).


I want to know how Linux-friendly this laptop is, and what works and what doesn't work.

If anyone else has tried this laptop with Linux, please tell me how Linux-friendly it was.



I will be highly thankful for any help you can give me.

Please reply to me early.


mastercoderx

---

### Post by vimalg2 on 2007-08-07
hi there mastercoderx,

Guess what!! i'm looking at the exact same machine when i discovered it at my local computer store.
I live in India and till yesterday my research was devoted towards Linux compatibility of the Acer Aspire 368x(3680/3682/3684/3684) series.

It looks like the Aspire 4310 is also based on the intel 940GML/945 g chipsets.

At the shop, i ran CPUZ on the 4310 demo machine to discover that ... HOORAY its got a Celeron M 520 procesor(which also incidentally is the entry evel 64 bit intel mobile processor, unlike pure x86 centrinos in the aspire 3683)

So if you feel like it, you can make the 64-bit transition in the near future.(I just thought you'd like to know that)
:-D

Here's the rest of the CPUZ info. The included 512 MB is a single DDR2 chip in slot1. That leave another RAM slot free for upgrades upto 
(2GB/4gb?) (for the 368x series, its  upto 2gb)


Next the problems I'm seeing....
The win xp driver information on the aspire 4310 indicated a "BROADCOM 4321AG" wi-fi adaptor was present (ref: Device manager)
The demo machine was running XP, so i couldn't get any other hardware info from the Linux kernel that is often demanded in this forum.

(on  a side note: Is this similar to the Broadcom 4310x wi-fi chipsets that are often debated on ubuntuforums??)

Upon looking underneath the laptop, I found a white sticker with more info
  "BCM94311MCG"

I dont know what broadcom chipset is actually in it. I'd guess the sticker info is probably more accurate.
I'm a noob as far as wi-fi is concerned(never used it before in my life)


I'd suggest you search on ubuntu forums for the threads regarding "acer 3680" intall on feisty to get a better idea of the steps to fix resolution via installing 915resolution or by installing new intel drivers for the GMA 950 graphics chip(i think? :()

... yeah and the 4310 was prominently showing off its DOLBY DIGITAL surround speaker system.(i guess its just fancy way of saying "i've got Intel HD audio codec+hardware in me!!"





If anybody has further inputs on this laptop, please add more info by replying in this thread.

refer here for specs
[http://global.acer.com/PRODUCTS/notebook/as4310.htm]("http://global.acer.com/PRODUCTS/notebook/as4310.htm")

she's a BEAUT!





So in summary, i'd reccomend

---

### Post by stchman on 2007-08-07
> **mastercoderx said:**
> Hi everyone

I'm planning on buying a notebook computer, which I plan to install (K)(X)Ubuntu 7.04 on.

I'm living in Australia.

I want a fully Linux-compatible notebook (or as linux compatible as possible).


I'm thinking of buying an Acer Aspire 4310-300508 [.]("http://global.acer.com/products/notebook/as4310.htm") notebook.

I want to know how compatible is this notebook with Linux.


The website says this notebook has Intel® GMA 950 graphics, so 3d acceleration should work good.




These are the notebook's specs:

Dolby Digital Sound

Intel Celeron M  1.6 GHz processor

512 MB RAM

14.1" wide LCD monitor

80 GB HDD

(note: these specs aren't from the website, they're from a magazine).


I want to know how Linux-friendly this laptop is, and what works and what doesn't work.

If anyone else has tried this laptop with Linux, please tell me how Linux-friendly it was.



I will be highly thankful for any help you can give me.

Please reply to me early.


mastercoderx

If you want a guaranteed Linux compatible laptop then go to Dell and buy one with Ubuntu pre-installed.

There is the laptop wiki:

[https://wiki.ubuntu.com/CategoryLaptop](https://wiki.ubuntu.com/CategoryLaptop)

You can also help your cause by making sure the laptop has Linux compatible hardware.

Nvidia video
Intel (pre 4965) or Atheros (5006EG or earlier) wireless
Realtek sound
Realtek ethernet

The Intel Centrino laptops are usually the most compatible.

Web cams and card readers are a sore spot with Linux.  Also the modem may or may not work as they are usually winmodems.

---

### Post by benson on 2007-08-14
I have this kind of laptop. I have installed Slackware 12.0, PCLinuxOS 2007, OpenSuse 10.2 and Puppy 2.17.

Internal modem & webcam were not detected. Slackware & Puppy detected wireless adapter (bcm43xx)  but cannot connect. Opensuse & Puppy have the highest resolution 1280x800.

So I will be downloading Ubuntu 7.10 Alpha and see if it can outrun the rest.

---

### Post by runtimedata on 2007-08-27
I have tried to get the Broadcom wireless working on the aspire 3680 but no luck.  Next try will be with ndiswrapper and the winxp driver.

---

