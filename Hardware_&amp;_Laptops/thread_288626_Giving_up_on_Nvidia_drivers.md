---
title: "Giving up on Nvidia drivers"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by jsnielsen on 2006-10-30
I've tried everything (I feel).

I tried the current NVidia Linux driver.
I tried the beta NVidia Linux driver.

I'm stopping gdm, then installing. At first, the NVidia installer gave me an error about not being able to find out which kernel module to use, and that I should install some libc and xorg sdk packages.

Ok, so I did, as the driver wouldn't work.

Now, the driver just races through, doesn't ask me for a thing, finds out which kernel module I need, installs it. Everything works fine.

I then do a gdm start. Yay, it starts ! And with the correct resolution (which is the reason I want the NVidia driver, since the default X only goes to 1024*768 it seems. As soon as I put on an NVidia driver, I get 1280x1024). At that point I'm in SU mode, since that's what it takes to install the driver.

Ok. Reboot.

Ubuntu 6.10 boots. Then it reaches the time for X to start. Three blinks (it goes completely black, then a cursor in the top left corner, then completely black, cursor, black, cursor) then an error message that I should check if I have an NVidia GPU in my machine. I have an NVidia 6800 card.

As soon as I use "nv" instead of "nvidia" in xorg.conf, I can start up the GUI, but only in 1024x768.

Does ANYONE have a suggestion on this ? Drivers install fine, they figure out everything by themselves. Then a reboot, and the xserver is broke, until I switch back to the built in nv driver.

I don't know what to do anymore.

---

### Post by patrickfromspain on 2006-10-30
You must uninstall the restricted-modules and the nvidia-glx packages and the do a sudo rm -rf /etc/init.d/nvidia*

---

### Post by jsnielsen on 2006-10-30
Allrighty then, I'll give that a go.

However - what's restricted modules, and how do I uninstall them ?
And how do I uninstall GLX ?

---

### Post by koshari on 2006-10-30
another option would be to use "envy"

this is a script to automaticly download the latest compatable source that suits your card and it will install it , modify your xorg.conf ect ect...

do a search of these forums there is a lot of info posted, 

there are 2 potentual pitfals, aparently it doesnt like some wifi cards and requires some big downloads,

---

