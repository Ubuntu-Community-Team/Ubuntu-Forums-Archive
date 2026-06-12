---
title: "ATI Radeon HD 4870"
date: 2009-07-26
forum: Hardware
---

### Post by php_penguin on 2009-07-26
From the title, I'm sure you can guess what I'm gonna ask..

**How do I get it to work?**
In Jaunty (9.04) to be specific, how do I get it to work properly, without the graphics going FUBAR, and the system actually working...

The tutorials I followed all ended in *rage* and i'n now on Windows 7 and seriously considering staying here... at least until the 10th virus ;)

---

### Post by PoopLoops on 2009-07-26
The jist is that the latest proprietary drivers from ATI work on an older version of Xorg than what Jaunty uses.  Open-source drivers are catching up, but you still probably won't get 3D support.

My card is slightly different, but what I did to get my Mobility Radeon HD 3870 to "work" on Jaunty was to completely purge anything having to do with the fglrx ATI drivers.  If you used apt to download it, I believe it has a "--purge" option (I'm assuming you can't even get to Synaptic, but if you can, just "mark for complete removal").  Then install the regular radeon drivers, and configure xorg to use them.

So, when you do dpkg-reconfigure xserver, it gives you a minimal xorg.conf file, right?  Find "vesa" and replace it with "radeon" after you've downloaded the driver.  If that doesn't work, try to download and use the radeonhd driver.  If *that* doesn't work, then I can't help. :(

I know what you mean, though.  I've actually grown to *like* Vista 64bit because I've been forced to use it so often.  Only reason I'm back to Linux for the moment is because programming is a lot easier for me, because the tools aren't so bloated like with the Windows "project" system and junk like that.  Which is stupid, because before getting this laptop, I was using Linux exclusively and having a great time.  Stupid ATI... :(

---

### Post by please on 2009-07-26
Yep, that's so ridiculous... we are promoting this hardware, the specs are open but this most non stable (software) hardware that we can get!

But yes, the opensource driver is making great improvement, the 2D is beautiful.

That's really a hard time to be a linux user, i forgot how big was the hardware frustration! My Thinkpad T42p and its freely working ATI Mobility shouldn't have died. :(

---

