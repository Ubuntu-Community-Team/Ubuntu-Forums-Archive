---
title: "Weird screen effects new Gateway Laptop"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by jmills on 2008-01-21
I have loaded Gutsy on a new Gateway T-6311.   (Set up to dual boot with Windoze Vista.)

Everything looks OK, except . . .

The top and bottom ribbons ("panels") are short - they stop about an inch from the right hand edge of the screen, and the bottom ribbon is about a half inch above the bottom of the screen.

Wallpaper (brown Ubuntu regular one) fits the screen fine, so there is brown wallpaper that extends beneath the bottom ribbon and extends further right than the end of the top and bottom ribbon.

If I run an application, like firefox, I can push the window all  over the screen, even past the end of the top and bottom ribbon, or below the bottom ribbon.  So, the wallpaper is "seeing" the whole screen.

xorg.conf seems really normal.  And, again, judging from the wallpaper and mobility of applications, the entire screen is usable.

Just the ribbons don't extend all the way to the left edge of the screen and the bottom ribbon is not at the bottom of the screen.  Looks kind of like the wallpaper isn't "seeing" the same screen size as the two ribbons.

Any bright ideas?

---

### Post by TheDilettante on 2008-01-23
Yeah, I hear you.  I just bought a MT6728 myself, set it up for a dual boot with Vista, and it's doing exactly the same thing.

Interesting behavior: when I click the 'maximize' button in any window, it extends no further than the two default panels.  Also, the Ubuntu logo displayed during load was obviously stretched out of its normal proportions.

I ran the restricted drivers manager, and installed nvidia-glx-new vaguely hoping nvidia was to blame (if this is in fact totally wrong, well, being a dilettante and all...)  Each time no change occurred.

Is it possibly a Vista+Gateway thing, like just the most hostile to Ubuntu combo ever or something?

Anyone reading this - any suggestions or pointers?  Clearly it's something related to the Gateway product line, or at least G's more recent models...  

Help!  Am saddened by this.


Edit:  More interesting behavior: when I try altering or changing resolutions the screen just goes black and hangs until I reboot the hard way.

---

### Post by TheDilettante on 2008-01-23
J, some things:

What does your xorg.conf look like?  Could you post it?  I'm interested because we both have an Intel Accelerated... X3100 chip, and there have been problems with the device or its drivers or both being successfully recognized automatically.

Also, have you tried moving your panels around?  I moved the bottom panel to the side and then back, and now when I reboot the bottom pane stays at the screen's bottom.  Moreover, having shown any application (i.e. firefox) that the screen is larger than the panels' default settings, it will now load in the entirety of the screen.  Not so for the top, and also the login manager is exactly the same.

In your Screens and Graphics Preferences (System -> Preferences), do you also have the values:

Model: Plug 'n' Play
Resolution: 1024x768 (but no higher) at 30Hz (also no higher.)

And, in the Graphics Card tab, are the devices recognized as being GM956?  or are they VESA drivers (generic)?

Because I think the Res. settings should be able to go higher, and that Ubuntu is having some real trouble recognizing what we're using.

Generally:

Anyone here have any advice or info re: the interaction between this graphics chip and gnome?  In text only mode the entire screen is used, so I think there must be some miscommunication that seems to be, to some extent, resolvable by 'showing' the machine its initial estimates are wrong.

---

### Post by TheDilettante on 2008-01-23
OK.  It's solved.  Do this: [http://ubuntuforums.org/showthread.php?t=610407](http://ubuntuforums.org/showthread.php?t=610407).  This is in fact a very popular problem.

Also, everyone, I'd like to apologize for thinking so verbosely out loud.

---

### Post by jmills on 2008-01-23
Absolutely works.  

You guys are gods.

I will look over the xorg.conf file later.  Must be some tweak there.

---

