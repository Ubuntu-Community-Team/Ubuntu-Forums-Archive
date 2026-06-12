---
title: "can a software destroy a piece of hardware?"
date: 2005-12-21
forum: Hardware &amp; Laptops
---

### Post by makis on 2005-12-21
My question is if it is possible, kernel or display managers or any other piece of software to conflict with a piece of hardware in such a way that it will destroy this hardware.

For example, I have a brand new Intel 64bit  PC, and try to install 32bit ubuntu 5.10. Apart that I come on black frozen screen just after the splash screen, I find my HDD to be 20GB less than the 250 I bought it.

Can kernel, or ubuntu in general destroy in any way a piece of hardware (i.e. the boot loaders of my HDD), or I have to check out only for hardware problems?

Is, finally, theoretically, software such a dangerous think??:confused:

Thank you very much!!

---

### Post by 23meg on 2005-12-21
It's very very unlikely; the one place it can be suspectible is monitors, where misconfiguration may damage a monitor, but even that is very unlikely with modern hardware.

I don't get your problem; was your hard disk "destroyed"? From your description it sounds to me like you seem to be missing part of it; is it 20 GB less than its reported capacity before, or its advertised capacity? In which OS are you seeing this? Keep in mind that the formatted capacity of a HD is always less than the advertised capacity.

---

### Post by PsyberOneZero on 2005-12-21
To find out the REAL size of a hard drive, use this formula:
**(Pretty Size * 1000000)/1048576**

250 * 1,000,000 = 250,000,000
250,000,000 / 1,048,576 = 238.418579102...

Pretty Size: 250 GB
Real Size: 238 GB

---

### Post by matthew on 2005-12-21
This is a very good read that will help to explain the discrepancy:

[http://en.wikipedia.org/wiki/Gigabytes](http://en.wikipedia.org/wiki/Gigabytes)

---

### Post by makis on 2005-12-21
Thank you very much all for your response.

@23meg : The situation is as follows:

I had purchased a month ago a new PC and I had difficulties in installation of ubuntu 5.10.When I could manage a successful one, after a period (some days), I suddenly could not boot anymore and my HDDs were found with significantly lower capacity. Finally, it was a complex problem, starting from the power supply unit, which at the end destroyed three HDDs and the Ethernet (onboard) card until we find out what was going on.

As I could not trust the motherboard, I built up a new machine: New Intel Dual core 64-bit processor, motherboard, HDD and an nVidia video card (the previous one had the video card onboard).

I tried to install ubuntu 5.10 successfully. I apt-get update and upgrade my new PC and everything was fine. I installed NVIDIA drivers and &#8211;apart that I lost the sound- on restart I faced a frozen black screen, just after the splash screen.

After that, every time I was trying to make a format and new installation of the ubuntu I was experiencing the same black frozen screen, without let me go in ubuntu even for the first installation time. 

Frightened that I may have the same problems I suffered with the previous PC, I bought a new HDD, to check it out. The installation went fine and after restart, I reached again the black frozen screen (without nvidia drivers this time). After that, again, I am unable to make an installation and to go in ubuntu (black frozen screen comes first). In this stage even the live CD does not play!!
 
I am confused. Why in a clean HDD I can do an installation for first time and I reach this frozen screen after restart? Why after that I cannot do an installation again?( I experience this frozen screen before even go inside gnome)

Because of these, I thought that it would be again a matter of destroyed HDDs and I posted this tread.

Now, I am thinking three things:

a)    is a matter of video card drivers
b)    is a matter of Xorg
c)    is a matter of both of the above.

Do you thing anything else? I need even a direction, what to look for.

Thx again!

---

