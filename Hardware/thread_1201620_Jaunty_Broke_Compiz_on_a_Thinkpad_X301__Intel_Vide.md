---
title: "Jaunty Broke Compiz on a Thinkpad X301 / Intel Video"
date: 2009-07-01
forum: Hardware
---

### Post by sog on 2009-07-01
Both Hardy and Intrepid supported Compiz effects on the Intel video hardware on board my Thinkpad X301, as did Jaunty initially. But after a repository update a few weeks back, Compiz effects are no longer available. I've tried various remedies, but so far have had no luck re-enabling them. 

Problem: 
Preferences: Appearance: Visual Effects
Clicking either "Normal" or "Extra" triggers a window reading "Searching for available drivers" and then a second window saying "Desktop effects could not be enabled".

Hardware: 
Lenovo Thinkpad X301
lspci reports video hardware as: 
VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
Thinkwiki.org reports video chip for the model as:
256 MB Intel GMA X4500HD onboard graphics 

Solutions tried to date:
1. Running 2.6.30 kernel
2. Running latest X.org PPA releases
3. Running latest Intel 2.4.1 video driver
4. Reverting to Intrepid video drivers

Progress:
None. I've been entirely without Compiz effects since the update, and have had no success in restoring them.

Any help/advice/thoughts appreciated.

---

