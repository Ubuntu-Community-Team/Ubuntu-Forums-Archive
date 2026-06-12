---
title: "Laptop touchpad: Can I emulate a 5-button mouse?"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by Krusz on 2007-07-22
So, I am starting to delve into the world of linux, and I knew if I went for a dual-boot I'd probably just end up using windows, so I recently picked up a new HD for my Toshiba Satellite A135-S4527 and installed Ubuntu 7.04 . Anyway, in windows, one thing that I really liked was being able to map the touchpad so that I could tap the top left corner and that would act as the "4" (far left) button on a 5 button mouse, and tapping the top-right corner would act as "5" (far right button). I liked this because it lets me move backward and forward through my visited pages in firefox simply by tapping TL for back and TR for forward. I have been searching around for a way to make it work, but so far I haven't found an answer. Also, I like mapping the bottom right corner to act as a middle click when I tap it, but right now it seems mapped to being a right-click. I have found some solutions to change that one, but so far they haven't seemed to work.

Thanks all!

---

### Post by linuxwizard on 2007-07-22
This might be what you are looking for

[http://gsynaptics.sourceforge.jp/](http://gsynaptics.sourceforge.jp/)

---

### Post by Krusz on 2007-07-23
As far as I can tell, that program does not allow one to set tap zones and define what those zones do. I also downloaded one called qsynaptics that seems to have a few more options than that one, but still nothing for 5-button emulation,

---

### Post by Krusz on 2007-07-24
Hmm, still looking... Also, my maximum (actually, my only) screen resolution in ubuntu is 1280x800, but in windows I can get 1600x1200. Any advice?

---

### Post by strabes on 2007-07-24
**Touchpad:** I think you'll need to edit some options in the synaptics touchpad section of your /etc/X11/xorg.conf file. Check out [this page](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad) from the Gentoo Wiki which contains tons of information about tweaking your touchpad. I believe these are the options you'll be interested in:

>  RTCornerButton (Integer): 	 Which mouse button is reported on a right top corner tap. Set to 0 to disable.
RBCornerButton (Integer): 	Which mouse button is reported on a right bottom corner tap. Set to 0 to disable.
LTCornerButton (Integer): 	Which mouse button is reported on a left top corner tap. Set to 0 to disable.
LBCornerButton (Integer): 	Which mouse button is reported on a left bottom corner tap. Set to 0 to disable.
TapButton1 (Integer): 	Which mouse button is reported on a non-corner one-finger tap. Set to 0 to disable.
TapButton2 (Integer): 	Which mouse button is reported on a non-corner two-finger tap. Set to 0 to disable.
TapButton3 (Integer): 	Which mouse button is reported on a non-corner three-finger tap. Set to 0 to disable.

**[EDIT]** I just tried setting my touchpad buttons like this: > 
	Option	    "RTCornerButton" "4"
	Option	    "RBCornerButton" "3"
	Option	    "LTCornerButton" "5"
	Option	    "LBCornerButton" "2"

The "4" generates a "scroll up" event and the "5" generates a "scroll down" event, instead of the more logical and useful back and forward events. The "2" event generates a middle click, and the "3" generates a right click. **Does anyone know how to map the top left and right corners to function as back/forward buttons?**




**Video Resolution:** This could result from several things. Check out the "Fix Screen Resolution" links in my signature; they have worked for basically everyone. Most likely it is because of the lack of proper video card drivers. If you have an ATI card the easiest (best) way is to just follow [this guide](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b) to install the proprietary ATI driver, called fglrx.

---

### Post by EricDB on 2008-02-06
> **strabes said:**
>  **Does anyone know how to map the top left and right corners to function as back/forward buttons?**

Same question here.  I have no problem mapping corner taps to right- or middle-click, but I haven't been able to map them to forward/back in Firefox.  I tried setting them to "6" and "7", but it had no effect.

---

