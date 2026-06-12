---
title: "Can't install Nvidia drivers"
date: 2009-04-24
forum: Hardware
---

### Post by geovino on 2009-04-24
When trying to install Nvidia drivers for Kubuntu 9.04 I get this error:

Sorry, the Jockey backend crashed. Please file a bug at: ubuntu-bug jockey-common Trying to recover by restarting backend.

Is this something that will be fixed in the next updates?

How else to install the Nvidia 173 drivers?

---

### Post by cwbar_1 on 2009-04-24
The same thing happened to me yesterday.  I restarted the system and finally got the driver to load.  (I think the heavy volume the Ubuntu servers are under at this time may be the problem)

---

### Post by geovino on 2009-04-24
> **cwbar_1 said:**
> The same thing happened to me yesterday.  I restarted the system and finally got the driver to load.  (I think the heavy volume the Ubuntu servers are under at this time may be the problem)

I figured as much. I'll again later or tomorrow. 

Thanks

---

### Post by simonsonjh on 2009-04-24
Same error for me too.  I'll keep trying and hope it is due to a slow network.  Users should still never see such an error message, nor should and backend be crashing.

---

### Post by geovino on 2009-04-24
I checked it again and it now says that the drivers are installed. Great, but the cube and scale which are the only two that I use don't work yet, even though in settings is shows the enable desktop effects is checked off. I rebooted and still no changes. What else is needed?

---

### Post by MockY on 2009-04-24
I have installed Jaunty on 5 systems now, all with Nvidia graphic cards, and I receive "the Jockey backend crashed" in ALL cases. This is obviously a bug and a bug I hope they resolve asap.
I did not even bother upgrading my laptops since they all use Intel graphics, and in Jaunty, the Intel drivers makes the system sluggish. It seems like Jaunty has serious graphic issues and if this continues to be the case, this untamed Jakalope will go down in history as yet another release that did not manage to improve in quality since Gutsy. It's a pretty sad trend that I hoped would stop now....looks like it didn't  :(

---

### Post by cwbar_1 on 2009-04-24
Go to the Synaptic Package manager and install the package "ccsm."  (simple compizconfig settings manager application) This will enable a 4th choice under System > Preferences > Appearance > Visual effects.  You can then activate all you want.

---

### Post by geovino on 2009-04-24
> **cwbar_1 said:**
> Go to the Synaptic Package manager and install the package "ccsm."  (simple compizconfig settings manager application) This will enable a 4th choice under System > Preferences > Appearance > Visual effects.  You can then activate all you want.

I tried it... it doesn't work now. Maybe too much traffic.

What I've seen is Ubuntu runs great. Xubuntu runs well too. Kubuntu is the least of the three from what I've seen. I'll keep trying though!

---

### Post by geovino on 2009-04-26
Was able to download drivers. Now I'm trying to enable desktop effects. It is checked off as enabled but it doesn't work. What else is needed to turn on compiz effects?

---

### Post by dannybuntu on 2009-04-27
Aw crap me too..

In Upgrades....always prop video cards. *sigh*

---

### Post by cwbar_1 on 2009-04-27
At the top of the Simple Compiz settings manager there is a drop (profile) down box that lists default, advanced, medium, minimal, and ultimate. If you tic "ultimate" then click the check mark, you can enable extra annimations and cube rotations.

---

