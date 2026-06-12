---
title: "Radeon X1250 in Karmic Koala Problem"
date: 2009-12-19
forum: Hardware
---

### Post by stark222000 on 2009-12-19
I've been searching the forums for an answer to this problem and i think the answer is "not yet or never", but my question is, Is there a driver for Radeon X1250 that i can use?

I have tried to play Portal and it can't even load up the title screen without crashing. Is there a way for me to get a driver for it because in the Hardware Drivers section there is only one for my wireless card. I tried getting the newest one from the AMD site but they stopped supporting it so when i try to install it it has an ERROR: kernel not supported and stuff like that.

I have reinstalled Ubuntu numerous times thanks to my **** ups of trying to install a working one because it will go to the text based login and i have no idea how to fix that. If anyone can help that would be fantastic.

---

### Post by stark222000 on 2009-12-22
bump

---

### Post by stark222000 on 2009-12-23
well i have a more refined question now. how can i go back to the old open source drivers i had? anytime i try to uninstall the catalyst software thing and install all the xserver-xorg things when i reboot it is a black screen so i have to reinstall the catalyst thing from the command line. so before i could use the wobbly windows and all that stuff but now when im on the catalyst thing (which apparently doesn't support my graphics card) it says it can't do it. also when i do aticonfig it says no adapters found. any solutions?

---

### Post by h2z on 2009-12-28
What version of catalyst have you been trying to install? ATI has stopped supporting some of the older (legacy) GPU's, including the X1250. The last catalyst driver to support X1250 is 9.3 ([get it here]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English")). 

I have had no luck with my mom's pc yet but I just saw your other post :@

---

### Post by Piscicani on 2009-12-28
Sorry, but Ubuntu 9.10 Karmic is not supported by Ati Catalyst 9.3 because of the  X server 1.6 then no 3d acceleration for you. Last supported X server is 1.5.X used on intrepid and jaunty.

---

### Post by h2z on 2009-12-30
So which drivers should be installed when using Karmic and radeon X1250 integrated?

---

### Post by Yellow Pasque on 2009-12-30
The open-source ati/radeon driver is pre-installed..

---

### Post by h2z on 2009-12-30
Is that any good?

---

### Post by night-wing on 2009-12-30
No. It's awful slow. I have the same card...

---

### Post by Reverend_Black on 2010-01-13
Hi,
In a similar vein; I'm also running the x1250 and karmic with the the radeon driver. Does anyone know how to get audio over HDMI working? Thanks.

---

