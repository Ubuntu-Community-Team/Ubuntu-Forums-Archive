---
title: "HP pavilion DV6000 and a few ubuntu problems"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by TBOL3 on 2008-01-16
Well, I got a HP Pavilion dv6000 for Christmas.  It is Intel based, 1.5 (or 1.8 Ghz) 160 GB, and vista yuck.  However, I'm having several problems with it.

I'd like to try to tackle the problems 1 by 1.

So first, flash won't work.  I've tried everything.  And I can't see anyone else with this fonominon.  I installed, re-installed, and installed with multiple package managers flash.  However, it still won't work.  Firefox always says, "Install additional plugins", so I click on it, and then I choose Flash (Gnash works, but is unusable).  Then it tells me flash is already installed.  And reloads the page with the "install additional plugins".  (If flash isn't installed it installs it, but I still get the same problem.

Please help me with this.  If it doesn't get resolved, I may have to occasionally (gulp) boot back into vista.

Thank you

Edit:  BTW please don't just give me [https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)) because I've already been there and I can't find anything there.

Thank you again

---

### Post by TBOL3 on 2008-01-17
Anyone, please.

---

### Post by Yellow Pasque on 2008-01-17
I'm assuming you're not using the AMD64 version of Ubuntu. If you are, look in the x86-64 forum for the solution.

do this:
```
sudo apt-get remove flashplugin-nonfree
```
Now download the plugin from Adobe's site ([http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)). Use the .tar.gz package. Extract it and follow the instructions.
When you restart FF, Enter about:plugins in the URL bar to verify that it's installed properly.

---

### Post by TBOL3 on 2008-01-17
Wow, thank you.

So what happened, why didn't the ubuntu package work?


And now, let's get onto my second problem.

Compiz (desktop effects) won't work.  No, it's that I need it, but it sure does look nice to have them.  I first tried to get them to work by using the simple appearances menu, it said that it couldn't turn it on.  So I downloaded the advanced controller, and it still didn't work.  Any help please.

Once again, thank you.

---

### Post by Yellow Pasque on 2008-01-17
> Wow, thank you. So what happened, why didn't the ubuntu package work?
You're welcome. I have no idea why the included package doesn't work, I just know that it often doesn't. You can probably look through Launchpad and see all the bug reports about Flash.

As for Compiz, what video card do you have? Use (sudo update-pciids; sudo lspci | grep VGA) if you don't know. Also, what does your /etc/X11/xorg.conf file look like?

---

### Post by TBOL3 on 2008-01-17
My graphics card is Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c), and I looked into the xorg file, but I don't know what to look for.

---

### Post by Yellow Pasque on 2008-01-17
You can't run Compiz with that graphic card, because it's blacklisted from doing so. For more details:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/148247](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/148247)

---

### Post by TBOL3 on 2008-01-17
Oh rats.

Oh well, next thing.  The internal microphone won't work, any suggestions?

---

### Post by Z_o-s-o on 2008-01-18
Wow seems like alot of trouble for a DV6000.

Intel processor I assume.

I've got an AMD DV6000 with an Nvidia chipset and everything worked out of the box, save for wireless.

---

### Post by TBOL3 on 2008-01-18
lol, that worked almost seamlessly for me.  (The key that I used is hexidesmel, and my card insists that I use ASCII, but by toggling between the two, it works.

---

### Post by TBOL3 on 2008-01-18
Anyone on the microphone issue?

---

