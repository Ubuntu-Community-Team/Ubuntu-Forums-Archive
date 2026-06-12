---
title: "[SOLVED] Nvidia Graphics output trouble"
date: 2008-08-09
forum: Hardware
---

### Post by MunkyJunky on 2008-08-09
I used to run 2 computers: a linux desktopping one, and a windows gaming one. I've recently upgraded my motherboard, so now I can run stick my Nvidia graphics card into my linux machine (my old one had no PCI-E slot, and my windows one with it was an MSI P965 Neo board, that has MAJOR issues running Linux). 

So now, I have all my decent hardware bundled up in one machine, and I've scrapped the older parts. Good thing is, no more Windows for me! Bad part is I can't actually get my Nvidia graphics card working. My new board is a Gigabyte GA-945GCM-S2L/S2C (S-Series). This has an onboard graphics chip. 

When I installed Hardy yesterday, I was never prompted to install the Nvidia restricted drivers. currently, im using the onboard graphics for output, and the monitor on my Nvidia card has no display. Does anyone have any idea how I can switch my graphics output from onboard to the Nvidia card? 

I attempted to manually install the binary drivers using this guide: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) , but the command 'lspci | grep -i nvidia' prints nothing, so I'm a little stumped on how to continue. 

Anyone got any ideas?

---

### Post by phidia on 2008-08-09
First what does > lspci | grep VGA entered in a terminal outputs?

We want to see if the system finds your other card. 

Also you say > the monitor on my Nvidia card has no display I'm not sure you can have both cards outputting at the same time, and if there is a way to turn the onboard card off it would be through bios-I think.

But let's see what that 1st command I provided outputs.

---

### Post by MunkyJunky on 2008-08-09
Well if both wont output at the same time, I'm not too fussed. I just want my Nvidia card going. My first thought would be to alter something in BIOS, but I couldn't find ANYTHING for it.

Terminal command outputs ```
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

```

---

### Post by MunkyJunky on 2008-08-09
I found the problem - I had been careless when I was fiddling with the machines' guts. **I had forgotten to plug the graphics cards' power supply back in!** :roll:

Plugged it back in, and every thing's going now. Restricted drivers popped up, running off the Nvidia card. 

I do the silliest of things sometimes... :)

---

### Post by schurtek on 2008-08-09
Just for the record... nvidia and ati cards can be a bit bothersome, but there is a cool tool to do the work for you... it's called ENVY... just search the repository for ENVY and install the one for your desktop... if you are using 8.04 then you need ENVYNG.

---

### Post by skliarie on 2009-08-05
> **MunkyJunky said:**
> Plugged it back in, and every thing's going now. Restricted drivers popped up, running off the Nvidia card.

Can you do lspci and see if you see the onboard Intel VGA card?

I have the same Gigabyte 945GCM-S2L motherboard and want to use both onboard and PCI-X ATI card, but for some reason PCI-X card always disables the onboard video card, disregarding video cards order option in BIOS.

Is there a way I can use both video cards at the same time?

---

### Post by skliarie on 2009-08-05
Disregard my last post. Looks like it was done by design (search for "onboard VGA":

[http://america.giga-byte.com/FileList/Manual/motherboard_manual_ga-945gcm-s2l(s2c)_e.pdf](http://america.giga-byte.com/FileList/Manual/motherboard_manual_ga-945gcm-s2l(s2c)_e.pdf)

---

