---
title: "xserver problems"
date: 2008-10-20
forum: General Help
---

### Post by rmhamm on 2008-10-20
Not really sure how it happened but my xserver became corrupted or erased and left me kinda screwed. I fixed it (maybe for now) by uninstalling then reintalling xserver via the commandline. but now things are acting funny. AWN doesn't have the icons correctly in the dock and advanced effects will not work. I have reinstalled my nvidia drivers as well and got my nice resolution back but still no rotating cube :(

What do I need to do to make sure that everything will go back to working correctly?

---

### Post by rmhamm on 2008-10-20
guess I figured it out.
Didn't see a solution earlier today but low and behold after I did my solution there appears solutions.
I reinstalled xserver.
I suppose I could of just reconfigured it but this worked alright too. unfortunately its messed up my compiz but I'll figure it out.

With as many people that posted this issue this had to be an update issue and not a user issue (just a guess).

---

### Post by cicatrix1 on 2008-10-20
> **rmhamm said:**
> guess I figured it out.
Didn't see a solution earlier today but low and behold after I did my solution there appears solutions.
I reinstalled xserver.
I suppose I could of just reconfigured it but this worked alright too. unfortunately its messed up my compiz but I'll figure it out.

With as many people that posted this issue this had to be an update issue and not a user issue (just a guess).

To get the cube, I always have to install compizconfig-settings-manager, and turn off "Desktop Wall" and enable "Desktop Cube" and "Rotate Cube".  There might be an easier way, but I like being able to tweak the other compiz settings anyway.

---

### Post by tuxxy on 2008-10-20
Your correct a reconfigure of the xorg should be sufficent, enable compiz at the desktop effects menu

---

### Post by rmhamm on 2008-10-21
I know how to install the effects and make them work but for some reason because of the reconfiguring of xorg and my nvidia drivers I can't make any of them work. I bet it has to do with the drivers and I'll switch to older drivers to see if they work.

---

