---
title: "Cairo-Dock and Startup Manager (uSplash)"
date: 2008-11-03
forum: General Help
---

### Post by kestal on 2008-11-03
I noticed a few things about 8.10 Intrepid the other day... Cairo-Dock is no longer functioning and you cannot change the Splash screens via Start Up Manager (Just does a text boot).

Any news? I mean, did Ibex change something to not make these work anymore? How are splash screens made now (manually, if anything)? Did the directories change or something? Is it a problem with Gnome?

Ditto with Cairo Dock.

There are a few threads about this but they were all left in the dust.

Edit: Used the deb off the main website and it works great (for the most part).

Still no luck on figuring out whats going on with usplash.

---

### Post by CheeseEatingBulldog on 2008-11-04
I have the same problems. splash screen doesn't work and Cairo dock has lost its 3d rendering. Under configuration and applets there are no options except 'preferences' which doesn't do anything when clicked.

How to fix?

EDIT:
I found that adding the official repo worked to update cairo-dock:
[http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#7-Ubuntu](http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#7-Ubuntu)

just substitute hardy with intrepid.

---

### Post by justacreep on 2008-11-04
I having the same problem with splash screens in 8.10. Also, my cube is not working in CCSM. It just looks like a wall when I hit <super>e..

---

### Post by VengefulIce on 2008-11-05
Good thing i am not the only one having problems with the USPLASH.

Mine boots and shuts down with text, no splash at all.
I think it is the EXACT same problem

---

### Post by noisan on 2008-11-10
Also having problems with usplash since I updated to Interpid, it will just show the regular text-based boot. Why?

---

### Post by noisan on 2008-11-11
Managed to find a solution thanks to Google. This worked for me running Interpid
- Uninstall the latest version of usplash and libusplash.
- Download usplash_0.5.19_i386.deb & libusplash0_0.5.19_i386.deb (easy to find with Google).

This should be the latest Hardy versions and they worked fine for me. Once installed just use startupmanager (sudo apt-get install startupmanager) and configure your usplash-theme.

---

### Post by Psyphre on 2008-11-26
How did you do that Noisan? 
When I try to remove upsplash and libusplash it wants to remove ubuntu-desktop aswell.

---

