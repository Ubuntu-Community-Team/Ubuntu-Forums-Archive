---
title: "Touchpad driver / behaviour"
date: 2009-03-08
forum: Hardware
---

### Post by Mats E on 2009-03-08
Hi,

the touchpad on my laptop has an annoying behaviour/response. If Im guiding the cursor with one finger on the touchpad, and happen to touch the pad with another finger (accidentally), the cursor jumps to a completely different location on the screen. On my other laptop (windows), accidental touches with a second finger do not disturb much or at all an ongoing movement with my first finger. Is this a driver issue, or can it be configured somehow?

Thanks,
Mats

---

### Post by InspiredIndividual on 2009-03-08
I think the easiest solution is to disable your touchpad while typing. In the following thread you can find this nice trick, search for 'touchpad': [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Mats E on 2009-03-08
I read about that feature, and seems interesting. However, my problem is really that the touchpad buttons are located so close to the touchpad itself that I keep double touching the pad even while not typing.

---

### Post by InspiredIndividual on 2009-03-10
A couple of possible solutions:

Can you succesfully edit your touchpad sensitivity settings in System > Preferences > Mouse ?

If that doesn't work, check the following guide to Synaptics Touchpads. It gives a bunch of information on editing your touchpad settings. Sensitivity is surely amongst the possibilities to edit. 
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

The second method (using gsynaptics and synclient) seems to work quite well for most users. There are several threads in these forums about this topic. A simple search should go a long way towards helping you when you encounter problems. It goes without saying that I'll be happy to try and help you as well if you've got any problems getting gsynaptics/synclient to work properly.

---

