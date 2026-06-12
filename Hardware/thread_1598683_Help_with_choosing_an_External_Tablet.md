---
title: "Help with choosing an External Tablet"
date: 2010-10-16
forum: Hardware
---

### Post by TuxIsAwesome on 2010-10-16
Hi, this is actually my first post here.

I am looking into getting an external graphics tablet, however I don't know which one would work best with Ubuntu

I've read Wacom tablets work really well, but need a bit of manual work to get them to work.

I run Ubuntu 10.04 Lucid Lynx 64-Bit, Kernel Version 2.6.32-25-generic. My hardware is a 4th Gen White 13" Macbook (4,1 to be exact).

I know most tablets work with OSX, but I use Ubuntu more than anything else, and I love it more than anything else on this machine.

Here are a few tablets I'm looking into. Just wanted to hear others feedback on how they work

**[FONT=Times New Roman][SIZE=2]Genius G-PEN F610 Ultra slim graphic tablet[/SIZE][/FONT]**

[http://www.amazon.com/Genius-G-PEN-Ultra-graphic-tablet/dp/B000WEHJHG/ref=pd_sim_e_4](http://www.amazon.com/Genius-G-PEN-Ultra-graphic-tablet/dp/B000WEHJHG/ref=pd_sim_e_4)

**[SIZE=2]Wacom Bamboo Pen Tablet[/SIZE]**

[http://www.amazon.com/Wacom-CTL460-Bamboo-Pen-Tablet/dp/B002OOWC3I/ref=pd_cp_e_2](http://www.amazon.com/Wacom-CTL460-Bamboo-Pen-Tablet/dp/B002OOWC3I/ref=pd_cp_e_2)

---

### Post by Favux on 2010-10-16
Hi TuxIsAwesome,

The Genius tablet is actually a rebranded Waltop tablet.  It's suppose to use the wacom driver, but there's a problem right now and it probably won't until Natty comes out.  The hot buttons on the tablet won't work, but you can get it working using the WizardPen driver for now.

The Wacom Bamboo Pen also works in Lucid.  But because it's so new the default wacom.ko (usb kernel driver) in Ubuntu doesn't work and you have to compile a newer one.  This isn't too hard.  Same goes with the xf86-input-wacom Xdriver.  The default is 0.10.5, which was early in it's development.  A newer one like 0.10.8 works a lot better and supports touch gestures.  But that only applies if you get the Pen and Touch.  The Pen should just need the wacom.ko.

So except for pressure being linear on the WizardPen driver and on a bezier curve for the Wacom driver the two tablets your showing should be about equivalent.  A Bamboo Pen and Touch would trump either.

---

