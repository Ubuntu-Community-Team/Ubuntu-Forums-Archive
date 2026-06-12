---
title: "Installing Nvidia drivers on UbuntuMATE 15.04"
date: 2015-05-09
forum: Hardware
---

### Post by MZ250Supa5 on 2015-05-09
After a bit if a sojourn on other distros, ( primarily Manjaro, promising, but with things breaking after almost every update, it has a ways to go) I have returned to Ubuntu now that Mate is an official release. It's nice to be back, but there are a few things that are really annoying me, such as the really frustrating experience I'm having trying to install Nvidia drivers so that I can use 3D graphics acceleration to full-effect. The nouveau drivers have come on a long way, of that there is no doubt, but they still won't allow me to use ultra graphics settings with full shadows on my OpenSimulator regions without there being extreme latency issues.  However, trying to install the nvidia drivers through Synaptic merely got a prompt to insert the 15.04 disk, which then won't go away after I've inserted the disk, and trying to install the drivers through the Software & Updates > Additional Drivers just results in the app apparently stalling. 

In the past it was a relatively straightforward process to install Nvidia drivers, so why is it now next to impossible? Or do I have to resort to installing the drivers manually? 

I know that sometimes regressions are inevitable, but surely a regression like this is a bit much?

I'd love to hear if anyone else has suffered with this issue, and knows of the solution.

---

### Post by dino99 on 2015-05-10
Except your complain, we still does not know what is your real issue and which card is used ;) not very helpfull if you wish to get help

nvidia is simple installed from the archive, either with 'synaptic' or via apt-get (example: sudo apt-get install nvidia-346)
note: each old nvidia installation have to be purged first, before installing a new version or reinstalling (to get rid of previous borked settings)

---

