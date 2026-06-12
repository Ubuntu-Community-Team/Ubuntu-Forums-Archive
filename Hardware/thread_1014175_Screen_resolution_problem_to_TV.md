---
title: "Screen resolution problem to TV"
date: 2008-12-17
forum: Hardware
---

### Post by staubsaugen on 2008-12-17
I have a Samsung 42in LCD and it has both a PC(VGA) input and HDMI inputs.  There's no actual DVI input on the TV, so I bought a DVI to HDMI cable, which is apparently the same signaling, just a different connector.  Well when I hook it up with the VGA cable, the graphics work just fine.  But when I plug it in as HDMI, The resolution seems to be really screwed up, and it looks like I'm only getting the top left corner of the screen.  Anyone ever try anything like this?  It's an XFX nvidia 9500GT graphics card.  I also have Windows XP installed and it works fine with DVI/HDMI cable and I've hooked up my Dell 20.1 inch widescreen flatpanel and that works fine under linux.  It somehow appears to not be detecting the TV properly when it's hooked up as DVI/HDMI.  I've also found [this]("http://www.x.org/wiki/FAQVideoModes"), and i've tried the modeline thing and that doesn't appear to fix my problem.  Any ideas?

---

### Post by neo37 on 2008-12-26
I have a similar setup and similar effects:
- Monitor is a Samsung Series 7 FullHD TV, which has both HDMI and VGA in
- PC has DVI (with Intel 945)

With a DVI-VGA adaptor, the monitor works fine at Full HD resolution 1920x1080. If I start up with a DVI-HDMI connection X will start, but the resolution is messed up, I see the background but the panel is somewhere off-screen. Fonts are too big. It's as if you would zoom in to an area of  the desktop.

Now, if I boot with DVI-VGA, and replug into DVI-HDMI after X is started, everything is fine. The text appears even sharper.
So DVI-HDMI would work fine, it's just a matter of getting it correctly set up. Obviously, the Intrepid auto configuration doesn't get things right with hdmi. A good xorg.conf might fix it, but how to arrive at a working xorg.conf if you have to start from the empty xorg.conf and displayconfig is gone?

Interesting is that with DVI-VGA I see two outputs in Xorg.0.log:
grep Output Xorg.0.log.vga
(II) intel(0): Output VGA has no monitor section
(II) intel(0): Output TMDS-1 has no monitor section
(II) intel(0): Output VGA connected
(II) intel(0): Output TMDS-1 connected
(II) intel(0): Output VGA using initial mode 1920x1080
(II) intel(0): Output TMDS-1 using initial mode 1920x1080
(II) intel(0): Output configuration:
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0):   Output TMDS-1 is connected to pipe B

But with DVI-HDMI, there's only one output connected:
 grep Output Xorg.0.log.hdmi
(II) intel(0): Output VGA has no monitor section
(II) intel(0): Output TMDS-1 has no monitor section
(II) intel(0): Output VGA disconnected
(II) intel(0): Output TMDS-1 connected
(II) intel(0): Output TMDS-1 using initial mode 1920x1080
(II) intel(0): Output configuration:
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output TMDS-1 is connected to pipe A

I've done some experiments with simple xorg.conf files, but 
no success yet. Would be nice if someone has some hints...

---

