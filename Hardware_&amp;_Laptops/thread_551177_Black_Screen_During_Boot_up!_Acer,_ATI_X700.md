---
title: "Black Screen During Boot up! Acer, ATI X700"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by MrMojoRising on 2007-09-14
Okay, This isn't your typical Black Screen problem that I've read about on the forums.:-k

I just did a fresh install on a laptop from the Feisty Fawn Alternate Install CD

When I boot up my laptop it goes to the GRUB menu. Then I pick my Ubuntu installation to boot from. Then during the entire boot up process the screen is blank. About 3-4 minutes later the screen comes to life with the GDM login window. I have full 3D acceleration once I log in. When I log out the screen is also blank.

So to recap I only have a black screen during boot up. Not after I log in.

By the way this happens no matter what drivers i'm using.


System Specs:
Acer Travelmate 4404 wlmi
ATI Mobility Radeon x700
Newest drivers installed via Envy

**So what's causing my blank screen during boot up?**](*,)

---

### Post by sloggerkhan on 2007-09-14
maybe try removing the splash screen from the grub bootline?

---

### Post by JC Casiano on 2007-09-14
You can also try removing "quiet" from /boot/grub/ menu.lst line.  One thing I have noted is that with Feisty during boot without "splash" and "quiet" the terminal character set looks like it is a bitmapped font.  In Edgy I would get a standard text screen font, then the font would change, suggesting a graphics mode change.  I added "vga=0x31b" to specify a higher density terminal.  So maybe that might work for you as well.

---

### Post by MrMojoRising on 2007-09-14
Okay removing the Splash option worked.

But I like the nifty splash screen.....how can i make it work?

---

### Post by sloggerkhan on 2007-09-14
No idea. Not even sure why it doesn't work. 

I'd look on launchpad and see if there's a bug report.

---

### Post by MrMojoRising on 2007-09-15
I did some messing around with the tool "StartupManager". This is a GUI fo editing the grub and gdm options. With this I was able to get some glimmer of hope.

Using the right resolution settings for the Boot Splash screen actually shows the fancy boot screen. Although it's off center and somewhat stretched out. 

I found that 800x600 @ 8bit color is stable. In fact all the way up to 1024x768 @ 16bit color seemed to somewhat stable although skewed.

It's a start....

---

### Post by tumbl3r on 2008-02-03
Check this thread [http://ubuntuforums.org/showthread.php?t=601326](http://ubuntuforums.org/showthread.php?t=601326).  It fixed my issue with black screen during boot and long boot times.

---

