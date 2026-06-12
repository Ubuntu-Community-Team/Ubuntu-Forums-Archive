---
title: "[SOLVED] Cairo-Dock sub-dock not retaining applets"
date: 2008-11-20
forum: General Help
---

### Post by Favux on 2008-11-20
I'm running cairo-dock v. 1.6.3.1 on Intrepid 64-bit from the BerliOS repositories.  Very pretty eye candy and since I have a tablet I like the fact that it rotates with the screen.  I've been learning how to configure it and now have it fairly customized.
  I tried to set up a sub-dock to contain the applets PowerMeter, ram-meter, cpu-usage, and nVidia.  Everything looks good until I reboot at which point all the applets are missing from the sub-dock.  I've put them back in and re-saved them again (in case something went wrong the first time).  No joy, applets gone again on reboot.  Can someone help me keep my applets from disappearing from the sub-dock (which I named system meters) on reboot?
  Could cairo-dock be saving the sub-dock to the old location rather than the new config location in home?

---

### Post by fabounet on 2008-11-21
you're applet are gone = they are in the main dock or definitely not activated ?

---

### Post by Favux on 2008-11-21
Hi fabounet,
That is correct, they're not on the main dock and they're no longer in the sub-dock, I have to reactivate them.  They then disappear when I reboot.  Any ideas?

---

### Post by fabounet on 2008-11-21
is your conf file writable ?
does it occur with any other applet, regardless their container ?

---

### Post by Favux on 2008-11-22
Hi fabounet,
  By the way are you the project administrator?  I think cairo-dock is great software and I appreciate your help.
Yes the conf file is writable and no it does not happen with any other applets.
I have "fixed" the problem by application of BFMI (brute force and massive ignorance).  I will try to outline the steps I followed as I remember them.
I tried to see if I could load one applet (cpu usage) into the sub-dock and then see if it would retain it through a reboot.  While loading the sub-dock I noticed again the sub-dock seem to want to go to the left and the left curved end was truncated.  I rebooted.
Applet was missing again.  At this point I decided to delete the sub-dock and start over.  After deletion the sub-dock docking plane appeared overlying the main dock with all four applets I had originally loaded on it (but the sub-dock, or at least its icon on the main dock was gone).  I rebooted.
Sub-dock with the 4 applets reappeared over the main dock surviving the reboot.  By the way I kept going into Cairo-dock configure to see what was going on and if there was a more elegant way I could find to handle this.  I then deleted all 4 applets (I probably should have gone to each applets preference and told it not to appear in the sub-dock and deactivated it in Cairo Dock configure).  The oval plane of the sub-dock remained hovering over the middle of the main dock.  I rebooted.
Now Cairo Dock appeared normal without the sub-dock.  I recreated the sub-dock using the gnome .svg icon and successfully loaded the 4 applets back into it.  I rebooted.  Success!!!  Applets retained in functioning sub-dock.
What I would like is to have this subdock to the right of the separator rather than on the left where it was placed by default.  But it seems I can't drag it to the right side of the separator.  I tried this before reinstalling the applets and it disappeared and I had to reinstall it.  Apparently a created sub-dock is supposed to stay on the left side, while the weather and compiz icon sub-docks can be on the right?
If this is true this may have been the cause of the problem because I had somehow dragged the original System Meter sub-dock to the right of the separator.  I looked back over the tutorial and some of the screen shots and I don't see a permanent separator, like my dock has, giving a left and a right side.  Hmmmm.
On a totally separate topic when I rotate my screen (I have a tablet PC) Cairo Dock isn't quite centered at the bottom of the screen.  It is a little to the right.  I noticed on the BerliOS site a script called Rotation (maybe written in Python?) without much description.  It seemed a little old.  Is it for tablet rotation?  Was it for addressing the/a centering problem?  Is it recommended?

---

### Post by fabounet on 2008-11-24
there is a patch that I didn't add yet, to handle screen rotation in live. I should do it.
you can place applets amongst launchers, there is an option in the Icon tab for that.
don't know why you had this problem with the sub-dock, I tried it with success. now if it works for you too, well that's good enough I think ^_^

---

### Post by Favux on 2008-11-24
fabounet,

I agree!  Everything is working great now.  The problem seems to have been a bizarre one-of.

I would love to see you put the rotation patch in.

Many thanks for your help.  I will mark this thread solved.

---

