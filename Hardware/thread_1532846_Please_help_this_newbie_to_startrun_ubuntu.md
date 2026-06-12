---
title: "Please help this newbie to start/run ubuntu"
date: 2010-07-17
forum: Hardware
---

### Post by zealkaiser on 2010-07-17
Hey guys!
I have a laptop which has core2duo processor, 4 gb ram, intel gm45 chipset with gma 4500mhd. On using command "lspci | grep VGA "it shows
Mobile Intel series 4 express chipset family

I am unable to run anykind of linux.
When i try to run fedora live cd it shows 'Address space collision', if i run open suse after booting the screen fluctuates and keep on flashing. Puppy starts but only in VESA mode

Since this is a Ubuntu form, let me talk about Ubuntu
If i run ubuntu 8.10 or 10.04 live cd it goes into a blank screen and freezes. Only ubuntu 9.10 runs on my laptop smoothly. All visual effects are also supported.
But i want to run 10.04. After searching on google i found a way to run it.
I use the command i915.modest=0 xforcevesa during the boot and it starts. But it runs in 1024x768 resolution since i have widescreen it stretches and looks ugly. I tried xrandr to use 1336x768 resolution but it shows an error something like "CRTC 0 FAILED". I even edited xorg.conf and added Subsection display with depth 24 and modes "1336x768" but nothing worked out.
One thing is for sure that the problem is my graphics card. It is also sure that if i can run ubuntu 9.10 perfectly than there must be a  way to run ubuntu 10.04 perfectly.

My another big problem is that i have a multigesture touchpad and neither of any linux detects it not even ubuntu. Without a mouse i can't do much to repair this graphics problem.

I also wanted to know that is hardware handled completely by kernel(does not need externel drivers to be installed like windows). I mean if 9.10 supports my graphics card then is it possible to use this kernel in 10.04 and then will it be able to support my graphics card.

Help me out guys.
Sorry for my bad english.

---

### Post by SebX86 on 2010-07-17
Didn't you mean 13**6**6x768 for your screen resolution ? 
This is normally the correct resolution for this kind of screen.

---

### Post by zealkaiser on 2010-07-17
Sorry, I mean 1366x768 resolution

---

### Post by zealkaiser on 2010-07-17
Today, I downloaded SLAX 6.1.2 and when I try to run, similary to Open Suse, after loading my laptops screen starts blinking, it keeps on fluctuating and the only way to exit is to power off the laptop

---

