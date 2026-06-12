---
title: "Hp Dv2610-us"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by BlaineM on 2007-10-15
has anyone installed Ubuntu on the HP Dv2610-us?  If so, what was your experience?  Any troubles, easy install?  I am thinking about buying one.  Obviously I want a machine that will not require me to go to extra extra lengths every time I install.  I like the hardware on this machine, and particularly I like the size of the laptop.

thanks for any feedback.

Blaine

---

### Post by BlaineM on 2007-10-17
has anyone installed Ubuntu on any of the new line HP laptops that contain the X2 dual core processor, and the mobile Nvidia video card?  Anyone?  There has to be someone in here?

Blaine

---

### Post by seantay00 on 2007-10-19
Blaine, the 2610 is an awesome laptop for the price it's at right now.  I have bought one and love it.  I will say I'm having some troubles getting ubuntu installed.  There seems to be some driver conflicts with both the Wireless Adapter as well as the Graphics card.  I think it will work, but I'm still doing some research.  It's frustrating because I installed Ubunutu on an old compaq and it was a breeze.

---

### Post by BlaineM on 2007-10-21
yeah, I was hoping to hear something along those lines.  Better to know I guess, than to buy the laptop, and have to use vista on it, the hog that it is.

I have had great success with Linux and laptops, I currently use a T30 and love how easy it has been to install anything.  Especially Ubuntu.

I hope development happens with this model and the parts that you need.  I am swinging to possibly getting a black Macbook, but would save $1000 by putting Ubuntu on an HP, or something.

From what I read though, the Intel Core 2 Duo out performs the X2 in many areas, although I probably would not realistically see the difference.

Blaine

---

### Post by HelloImHowie on 2007-10-29
I just picked up a DV2610us and I'm having a real hard time putting any version of linux on it. lspci lists most components as "unknown". It seems that there's no/little support for the nForce 630a chipset for now.

---

### Post by noisebeard on 2007-10-30
I'm having a ton of trouble with this laptop.  I can get Gutsy Gibbon to install with the alternate setup disc, and I can get the video loaded properly with the restricted drivers, but I cannot for the life of me get the Broadcom wireless to work with fwcutter or ndiswrapper.  lspci also states that 99% of the hardware is "unknown" resulting in me just flat out giving up.  It's discouraging too, having to use Vista until some ray of hope is seen.

---

### Post by seantay00 on 2007-10-30
Yea, I've given up for the time being.  Has anyone else had any success?  I'm hoping that the development crew can bail us HP users out.  The only live CD I've gotten to work is BT 2 Final.  It boots perfectly.  I've contemplated just running a dual boot of BT2 and Vista, but I'd love to have unbuntu back again.

---

### Post by agomp on 2007-10-31
What exactly is BT?
Thanks.

---

### Post by seantay00 on 2007-11-03
Back Track 2 Final- Security Auditing Linux Build.

Has anyone had any luck yet getting a successful install?

---

### Post by rampras on 2007-11-04
Check this out:

[http://www.megalinux.net/2007/11/hp-dv2610us-ubuntu-gutsy-gibbo.html](http://www.megalinux.net/2007/11/hp-dv2610us-ubuntu-gutsy-gibbo.html)

---

### Post by HelloImHowie on 2007-11-08
Well, that got me up and running for a little bit. It seems that after I boot once, it won't boot again. I've reinstalled ubuntu twice now and after the first boot it just hangs on the splash screen and dumps me to a busybox console. Anyone else have similar problems?

---

### Post by rampras on 2007-11-09
once it booted .. did you install the restricted drivers for Nvidia ? choose yes for all the restricted drivers. It should work

---

### Post by HelloImHowie on 2007-11-09
The first time I did, the second time I didn't. It's not a missing driver issue, it looks like it can no longer mount the hard drive after it boots once. I'll post the exact message when I get home later.

---

### Post by HelloImHowie on 2007-11-10
For some reason something keeps editing my /boot/grub/menu.lst file and changes my kernel root flag from /dev/sda2 to some random string of characters. Maybe updating the BIOS will help.

---

