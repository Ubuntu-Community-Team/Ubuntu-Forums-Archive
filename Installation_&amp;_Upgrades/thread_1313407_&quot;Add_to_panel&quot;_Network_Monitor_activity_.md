---
title: "&quot;Add to panel&quot; Network Monitor activity 2.26.0"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by ronux on 2009-11-03
Hello,

Does anyone know how to get a previous "Add to panel" item called Network Monitor (version 2.26.0 - 2003 Sun Microsystems) which was available on Ubuntu 8.10 and prior versions but not any longer available on 9.04 and up?

Many thanks,

R.

---

### Post by Unknown Pirate on 2009-11-03
The **notification area** come with network monitor.

---

### Post by ronux on 2009-11-03
See attached file.
I am talking about the "Network Monitor" with the underneath description "Monitor network activity". 
It looks like that it has been removed and I would like to know if there is a way to get it back. 

Thanks for any suggestion.

R.

---

### Post by akh00 on 2009-11-03
I figured out half of the solution for this problem. I need help on the other half! 

Open Synaptic Package Manager and search for "gnome-netstatus" and install the applet. Now all you have to do is add this applet to the "Add to Panel" list. But I don't know how to do that - so can someone help me on this please?

EDIT: I found out the solution - after installing gnome-netstatus from SPM, simply restart your system and you'll find the network manager once again in the "Add To Panel" List :) Hope that helped

---

### Post by ronux on 2009-11-04
akh00: You are very correct! The good old reboot did the trick :p
Note: the icon is different but Properties displays the same information.
Many thanks!

R.

---

### Post by KPDXHAM on 2009-12-05
> **akh00 said:**
> I figured out half of the solution for this problem. I need help on the other half! 

Open Synaptic Package Manager and search for "gnome-netstatus" and install the applet. Now all you have to do is add this applet to the "Add to Panel" list. But I don't know how to do that - so can someone help me on this please?

EDIT: I found out the solution - after installing gnome-netstatus from SPM, simply restart your system and you'll find the network manager once again in the "Add To Panel" List :) Hope that helped

I tried this 2 times now. Followed instructions exactly, reboot & all. The only thing I see is NetworkManager Applet 0.7.996 which is already installed.](*,)

Really would like to be able to see GUI of the network connection like I've gotten used to in XP.

---

### Post by ronux on 2009-12-05
That is odd.
Make sure that gnome-netstatus is properly installed.
Go to Synaptic, it should be checked.
Or maybe remove it completely and try installing again, and reboot.

Please remember that this is a manual add on. Therefore right click on the upper navigational bar > Add to panel > and you should see Network Monitor, then just add it. It will appear on the panel bar. 

R.

---

