---
title: "Krandrtray - no rotation left or right, tx1000 laptop"
date: 2009-04-13
forum: Hardware
---

### Post by chjornaq on 2009-04-13
I have a tx1000 laptop that I had just about given up on as far as any linux distro goes, only to give intrepid a whirl and find that almost everything works wonderfully.

The only thing keeping me from a full conversion from vista is the screen rotation.  I'm using KDE 4.2 on Kubuntu Intrepid, have activated the 180 nvidia drivers, with the Krandrtray applet running in the tray.  After adding 

Option "RandRRotation" "on"

to my (surprisingly slim) xorg.conf in the Device section, that gives me the option to rotate left, right and upside down in the Krandrtray menu, but the only one that actually works is the upside down option, but right rotation is the one I need.

Being this close to a nice, comfortable GUI solution, I'd rather not go the CLI and scripting route to solve this problem (my mom has almost the same laptop, so CLI is out of the question with her).  If anyone knows how to get Krandrtray to actually rotate right, it would greatly appreciated.

---

### Post by chjornaq on 2009-05-07
I almost have this figured out:

If I change the resolution to 800x600, I can also flip the screen left and right, but I end up with 800 pixels on the shorter height of the screen and 600 along the width.  So there's an automatic "flipping" of the resolution that I don't want.

The easy solution would be to give my screen an 800x1280 resolution (instead of its native 1280x800), but I have no idea how to do that in the newer versions of Ubuntu.

So my new question is how do I change my resolution to something weird like 800x1280?

---

### Post by chjornaq on 2009-05-07
Okay, one more update:

I found a setting in the (new?) nvidia-settings that allows for screen rotation that works perfectly the exact way I need it to, but I don't want to have to go into nvidia-settings every time I want to rotate the screen.  

The Help file for screen rotation says that that particular control panel "allows you to select the desired screen orientation through the XRandR extension".  

Does that mean I should be able to setup an alias to a script of some sort that uses XRandR, and if so, how do I do that?

---

### Post by Favux on 2009-05-07
Hi chjornaq,

This HOW TO should show you how, method 1 should work.  Since you're probably using evtouch you don't need the xsetwacom parts of the script, just the xrandr lines.  See:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)  As you see you can set it up in a launcher or bind it to a key.

Good luck!

PS:  If you need any more help with the scripts let me know.

---

