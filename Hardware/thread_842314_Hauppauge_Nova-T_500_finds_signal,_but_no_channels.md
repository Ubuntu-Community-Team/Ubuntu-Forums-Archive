---
title: "Hauppauge Nova-T 500 finds signal, but no channels"
date: 2008-06-27
forum: Hardware
---

### Post by japan on 2008-06-27
I'm having a bit of trouble with this card on Ubuntu 8.04. As far as I can tell it's installed and detected correctly (MythTV, Kaffeine, scan (aka dvbscan) and and w_scan can pick it up and scan with it).

At first I wasn't getting any signal at all with scan or w_scan, so I tried activating the on-board LNA as per [these instructions]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500#Forcing_the_activation_of_LNAs_.28Low_Noise_Amplifier.29").

That seemed to make a difference, since now I get a few "signal OK" results when I run w_scan, but it doesn't find any channels. Using the tuning data from w_scan with scan doesn't find anything either (I get a series of "filter timeout" messages).

Is this likely to be a signal strength issue? From searching around I've found a few people who have commented that the card needs a very strong signal, but I'm not sure how to go about determining how strong the signal is. Kaffeine has a signal strength meter, but I don't know how accurate or useful it is. Generally it doesn't display a signal strength higher than 40-50%.

Anyone have any experience with this, or similar cards? I'm tempted to go and get a signal booster and give that a try.

---

