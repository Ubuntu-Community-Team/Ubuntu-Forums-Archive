---
title: "Cannot Set Higher Resolution on External LCD"
date: 2008-05-08
forum: Hardware
---

### Post by dsk3801 on 2008-05-08
Ok -- first, I should note that this setup worked perfectly in 7.10, so I don't know what I'm doing wrong with 8.04.  Any help is greatly appreciated.

Did a fresh install of 8.04.  I run it on a Gateway laptop (with an ATI Radeon Mobility 1400) and an external LG LCD 19" Monitor.  I'd like to be able to turn on the laptop, close the lid, and use only the external monitor.

I installed the restricted ATI graphics driver and can use the "Extra" visual effects without any problems.

The only thing that is holding me back is the resolution on the monitor.  The best setting is 1280x1024.  Unfortunately, when I go to System > Screen Resolution, the only options are 1280x800 (the size of the laptop display), 1024x768, and lower.  There is no option for 1280x1024.

Funny enough, when I did the install (with the external monitor attached and the lid closed), it displayed it in 1280x1024.  On bootup, it also displays the Ubuntu splash screen with the little scrollbar in 1280x1024.  As soon as it gets to the splash screen, it drops me to 1024x768.

If you can offer any suggestions on how to get this to work, I'd appreciate it!

---

### Post by dsk3801 on 2008-05-08
oops... should have done a better forum search first.  In case anyone is curiuos, all I did was run this line in the terminal:

```

sudo aticonfig --mode2=1280x1024

```

Did a CTRL+ALT+BACKSPACE, logged in, and poof, the new resolution was listed and works perfectly.  Yay!!:popcorn:

---

### Post by mrodent on 2008-07-09
Hi,

I have a similar arrangement: 19" Iiyama LCD attached to a Dell laptop... want to close the lid etc.

When I boot up with the LCD attached a monstrously strange thing happens: the Linux desktop DOES display on the external LCD, but it is as if this piece of screen is a viewport on a much larger screen real estate which is the desktop... so as I move the mouse the LCD's display "scrolls around" what would be a huge 3-foot square desktop... so I only get to see a small portion at any one time... as dictated by the position of the mouse.  Meanwhile the laptop screen is fine, beautiful... but too small for comfort.

my graphics card is an ATI (don't have spec to hand)... I had to install a proprietary driver after weeks of head-scratching (am a NOOB).

so should I just run that command you gave?

anyone else know what I should do? do I maybe need a special driver for the make of LCD monitor? 

floundering... pls help

---

### Post by mrodent on 2008-07-09
Later...

inexplicable success: I did that "aticonfig" command, and I also disabled the ATI proprietary driver... and then rebooted.  At reboot the 19" LCD monitor displays OK!

There is still one problem though: the image ratio of the desktop LCD is not the same ratio as the laptop, and what it's currently displaying on the desktop LCD is a desktop area not much bigger than the laptop, with a large bit of background BELOW the taskbar... i.e. the taskbar (do we call it that in Linux) is floating about 2" above the bottom of the LCD screen.  Should I maybe tinker with that aticonfig line, mode3="[nnn]x[nnn]", or sthg???

anybody know where aspect ratio gets set in Linux?

Thanks

---

