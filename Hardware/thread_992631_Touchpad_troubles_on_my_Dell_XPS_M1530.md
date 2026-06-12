---
title: "Touchpad troubles on my Dell XPS M1530"
date: 2008-11-24
forum: Hardware
---

### Post by JaggedOne on 2008-11-24
I recently installed aGSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
 fresh copy Ubuntu 8.10 on my Dell XPS M1530. I have not been able to get the touchpad to behave. On the fresh install it would not work properly. Using it would cause the mouse to move and click randomly across the screen. Then after updating ubuntu it worked to an extent. However it was extremely slow. I did some googling and tried to fix it myself. I installed Gsynaptic. After doing everything I could to enable SHMConfig I still get this error when I try to start up touchpad prefrences.

> GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

Anyway after all my dicking around the touchpad is back to its orignal 100% broken state. Moving my finger across it causes it to randomly move and click across my screen.

I would really appreciate any help you folks could give me. I am a new ubuntu user. This is the only roadblock keeping me from switching over from windows entirely. I don't know what other information to give you that would help lock down the problem, so please ask me what you need and I would be happy to provide it.

---

### Post by __Ryan__ on 2008-11-24
I'm using a Dell M1530 to write this post in Ubuntu 8.10.  My touchpad experiences these problems sometimes when I open the lid but seem to go away soon afterward.

I have read that other users have experienced these same issues and that the latest BIOS fixes them.  I currently have A07, but I believe the latest version is A11 but anything after A08 should have the touchpad fix.

---

### Post by JinStevens on 2008-11-24
Gsynaptics requires SHMConfig to be enabled and under 8.10, the way to enable it is different than in 8.04.

Look here: [https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig](https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig)

---

### Post by jespdj on 2008-11-25
> **JaggedOne said:**
> I have not been able to get the touchpad to behave. On the fresh install it would not work properly. Using it would cause the mouse to move and click randomly across the screen.
This is a known problem. You'll have to add a kernel parameter: i8042.nomux=1

See [this thread](http://ubuntuforums.org/showthread.php?t=737060) for more information.

---

### Post by daberger on 2008-11-26
i had this problem to. i ended up buying a bluetooth mouse and using that

---

### Post by daberger on 2008-11-26
ryan 
i have an m1530 running 8.10 and windows and bios A09 and i still have the touchpad problem

---

