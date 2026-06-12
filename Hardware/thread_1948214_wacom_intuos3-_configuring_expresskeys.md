---
title: "wacom intuos3- configuring expresskeys"
date: 2012-03-27
forum: Hardware
---

### Post by caffeine. on 2012-03-27
I've been searching all over the internet for a good solution to this, and haven't found anything, but please direct me to an appropriate link if I've missed something.

I have a Wacom Intuos3 tablet that appears to work fine with GIMP aside from the expresskeys/touchstrips, so I've been trying to configure them on Ubuntu 11.04. (They work fine on Windows.) I've installed the linuxwacom drivers (xsetwacom -V shows 0.10.11) and tried a few versions of using xsetwacom to set the key bindings, but when I last tried (a few minutes ago), setting a key binding and then trying to use it would immediately crash xserver and log me out. Specifically, I was able to set a few keys (1 was shift, 2 ctrl) but then I tried binding a touch strip to "+" by using something along the lines of "key shift = " and that crashed it (so maybe I'm writing the key combination wrong?)-- the same happened when I set a similar key binding for a key rather than a touch strip. I also have kde-config-tablet installed, but the tablet configuration option doesn't seem to show up anywhere in my system settings menu or in compizconfig. And I tried using xbindkeys, but I couldn't figure out how to get that to bind my tablet keys instead of binding my laptop mousepad buttons. 

I'm not sure what I should do to resolve this. Potential issues I could think of were
- I don't have the right version of xsetwacom
- I'm not writing the key binding correctly
- I'm missing some other driver required for key bindings

If anyone knows how to resolve those potential issues or knows what the problem actually is, help would be much appreciated.

Thanks!

---

### Post by Favux on 2012-03-28
Hi caffeine,

Without seeing your xsetwacom commands it is hard to tell what the problem might be.  But for general information see:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)  from the mediawiki HOWTO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

That said 0.10.11 is getting kind of long in the tooth and 0.14.0 is out now.  There have been several touch strip fixes and pad button commits since then.  An important one after 0.14.0 came out, so I would clone the xf86-input-wacom git repository.  See the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") part II.

---

### Post by caffeine. on 2012-03-28
Okay, it seems like updating to 0.14.0 fixed my xserver crash problem, and I think that using "key plus" instead of "key shift =" will solve my key binding problem-- I didn't know that that was what I should be using. Thanks for your help!

---

