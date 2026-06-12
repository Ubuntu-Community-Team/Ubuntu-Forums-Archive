---
title: "Hardware problem: Braodcom DCM4318 Wifi adapter not recognized Ubuntu 9.10"
date: 2010-01-02
forum: Hardware
---

### Post by Tjibsson on 2010-01-02
I installed Ubuntu 9.10 as a newbie, on a HP Pavillion AMD Turion Laptop of a few years old. I used to have WinXP on this machine, but it has become too slow.
I want to use the laptop for viewing DVD-movies while commuting, but also do I want to take the opportunity to learn something about Ubuntu/Linux.\Got the DVD-thing figured out now, but the DCM4318 still doesn't work

Now for this problem: I can get my Wifi-adapter to work. I tried to install the item via Synaptic, but it didn't cover the Broadcom DCM4318 adapter. (bcm43xx-fwcutter installed, but then what?)

The LED on the hardware-button doesn't even light. I had it working under Presto-MypPC / Xandros though, that all went automatically.

Can anybody help this newby?

---

### Post by kevinatkins on 2010-01-02
Hi,

First off - you're going to need a working internet connection to your laptop before proceeding, so you'll need to have it plugged in via ethernet to your router.

From memory, you're going to need to enable the 3rd-party software repository, which contains the correct driver for your wireless card.

To do this, go to System -> Administration -> Synaptic Package Manager

You'll need to enter your password, then Synaptic will appear. Once in Synaptic, click on the Settings menu and choose Repositories. In the window that appears, click the 'Other Software' tab and place a check / tick next to the 'Partner' and 'Partner (Source Code)' lines. Then close the window. Next, you'll need to reload the repository lists by clicking the appropriate button in Synaptic. Finally, close Synaptic.

Once you've done this, go to System -> Administration -> Hardware Drivers. In the window that appears, you should now see your wireless card listed, which you can then activate.

For DVD playback, you're going to need the Medibuntu repositories - do a Google search on Medibuntu for further instructions..

---

### Post by Tjibsson on 2010-01-02
Kevin,

thanks for the swift answer. I had to revert to an English interface language to get the order of things to do right. I did all you suggested, but in the Hardware drivers-window I only get my modem/software modem, already in use (never used the thing though).
I saw some suggestions for the Broadcom DCM43??, being all other numbers then my DCM4318.
I have a quite normal HP Pavilion laptop of about 4 years old. Didn't think it to be something odd. I keep on looking and hoping to find or get a solution for this.

By the way, I got the DVD-thing going.

---

