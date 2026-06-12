---
title: "Major Widescreen Problems.  Help please?"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by queenhawkeye on 2008-01-11
I have a huge problem with Ubuntu.  [i'm running 7.04]

After my superlong frustrating install with ubuntu, it didn't detect my widescreen laptop display.
It was set to 1280x700 or something like that when Vista is set up as 1280x800.

I followed someone's instructions on the irc a while back, and now I can't get any display[no GUI; just the command prompt.].  It gives me a quick error message and then gives me a space where I can type commands and stuff.

At this rate, i'm pretty frustrated with ubuntu.  Can someone help me get it back my display and/or get me my much needed widescreen?  I'd be forever grateful.  :]

I have an acer aspire 5315-2153; intel celeron processor 530.

Thanks!

---

### Post by taurus on 2008-01-11
Try

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

p.s.  What kind of graphic card does it come with?

---

### Post by queenhawkeye on 2008-01-11
I have a Mobile Intel GraphicsMedia Accelerator X3100.  I'll try your suggestion in a bit.

---

### Post by queenhawkeye on 2008-01-11
Sorry for the double posting.

I just went through your commands and after i picked intel and chose my screen resolutions, i typed in startx and now i'm sitting at a black screen.

-Edit-

I rebooted it and now it doesn't even load the command prompt.

---

### Post by taurus on 2008-01-11
Boot into recovery mode from GRUB menu and run that command again.

```
dpkg-reconfigure -phigh xserver-xorg
```
This time, try using **vesa** driver.  Then, you can reboot your machine with

```
shutdown -r now
```

---

### Post by queenhawkeye on 2008-01-12
I tried using the vesa driver and then rebooting back into normal mode, I got the command prompt back but before that loaded it gave me an error message about xserver-xorg not configured correctly.

I remember it saying something about fatal server error signal 11.

I guess that's not good?

---

### Post by Auslegung on 2008-01-12
Don't mean to steal your post, Queen, but I'm having trouble with my widescreen and this is the only place in the forums I've found even remotely related.  My display was fine for months, then I went out of the country for a few weeks and the desktop and every program I run hangs off the edges of my screen by about 1-2cm.  Quite frustrating.  What can I do about it?

---

### Post by queenhawkeye on 2008-01-13
Can somebody please help me?  I'm really desperate.  At this rate, i'll end up getting rid of ubuntu.  [and then watch it kill my laptop slowly.]

---

### Post by queenhawkeye on 2008-01-20
I'm still looking for help on this issue.

---

### Post by Auslegung on 2008-01-20
If I were you I'd just re-install Ubuntu.  As for the widescreen problem I got mine fixed by just messing with all the configurations, restarting, etc.  It was a little frustrating and I'm still not 100% sure of what I did that worked, because I had been trying the same stuff for days and then BAM, it worked.  Good luck and don't give up on Ubuntu.  If you do, try again in April when they release 8.04.

---

