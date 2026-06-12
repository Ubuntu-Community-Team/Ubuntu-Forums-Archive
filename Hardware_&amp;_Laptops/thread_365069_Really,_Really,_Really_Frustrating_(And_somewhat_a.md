---
title: "Really, Really, Really Frustrating (And somewhat absurd) Monitor Problem"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by Pinball Machine on 2007-02-19
I'm quite new to the Ubuntu world and I thought a good place for me to experiment would be with my old iBook G4. About a year ago my son dropped the laptop and shattered the screen. Our quick fix for the time being was to just plug it into an old Dell monitor we had lying around until we got around to getting it fixed. We ended up just buying a new laptop and the iBook sat and gathered dust. So now I am quite excited about converting to Ubuntu and I go to install it and my monitor screen is gray. I can tell that it's working because the taskbar is visable in the 3x3x3 triangle of working screen in the top right corner. If someone would like to inform me how to fix this problem while essentially being blindfolded it would be of great assistance.

---

### Post by gradedcheese on 2007-02-19
Can you get a text shell?  Try pressing Control+Alt+F1 to get there.  I don't know what Control is on a Mac keyboard, but I'm sure it's... something :)

Now that you have a text shell, ask for a reconfiguration of X:

sudo dpkg-reconfigure xserver-xorg

and now switch to a graphical login (Control+Alt+F7, though F8 and up will also work).  Kill/restart X if needed (Control+Alt+Backspace) -- any useful results?

---

### Post by Pinball Machine on 2007-02-19
Ah, no luck. I don't even know if I have a text shell. but I'm pretty sure after trying it 10 times it ws a no go. Maybe it's just different keys for a Mac or something? I can see pretty much the full drop down menu of "Applications" and about half of the "Places" drop down menu, if that helps anyone. I think this is going to turn out to be an adventure in hotkeys though.

---

