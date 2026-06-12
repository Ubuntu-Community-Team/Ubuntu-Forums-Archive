---
title: "Dual-head (Sort of)"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by rmfought on 2007-04-20
I have an Acer Ferrari 4005 WLMi with a Radeon Mobility X700.  I just installed Feisty amd64 and I have to say, this has been the smoothest and best distro for this machine yet.  The graphics subsystem and audio works from the get-go - even the desktop effects.

What I really need though, is the ability to run the DVI-out as my primary display.  95% of the time, I run my laptop with the lid closed, hooked up to a DVI KVM with the rest of my boxes.  The optimum configuration would be one where I can with the click of a mouse change the display from the LCD to the DVI-out and back again.  I don't need them both on at the same time.

Currently Ubuntu is configured to use the "ati" driver (i.e. as opposed to the "radeon" or "fglrx" drivers) - is dual-head even possible with this driver?  Are there any applications out there (besides the ATI proprietary driver/tools) that make dual-head control easier?

Thanks and great work on Fiesty!  This might be the one that bumps WInders off my laptop!

---

### Post by mmendez on 2007-04-30
My needs are exactly the same as these. I have the same computer and I would like to use my Fn+F5 button that was made to do this very thing. Anybody have any thing figured out? I presently am using fglrx installed with feisty's restricted driver manager.

---

### Post by rmfought on 2007-05-03
I solved my problem, but I had to change from using the DVI port to the VGA port (and I am now using the fglrx driver, due to stability problems with the "ati" driver).  I wasn't getting full resolution out of the DVI anyway, the screen would flicker constantly at 1680x1050 since the video card is only rated to 1600x1200 DVI output.  I was forced to use 1400x1050 which is just a waste of screen real estate.

I added some command launchers to my toolbar to control the screen output:

For external monitor only:
aticonfig --enable-monitor=crt1, nolvds

For laptop screen only:
aticonfig --enable-monitor=lvds, nocrt1

For both:
aticonfig --enable-monitor=lvds, crt1

This also allows me to see the grub interface when the system is booting (I dual-boot with Windows), which I couldn't do when using the DVI port.

---

