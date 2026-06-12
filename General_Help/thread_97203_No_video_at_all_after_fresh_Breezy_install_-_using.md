---
title: "No video at all after fresh Breezy install - using NEC Accusync LCD 200VX"
date: 2005-11-30
forum: General Help
---

### Post by Roobert on 2005-11-30
Hi,

I just did a fresh Breezy install from an ISO image CD. The partitioning went fine, and I now have a dual-boot XP/Breezy PC. Upon reboot, Breezy boots up fine. I get "OK" for all the categories that scroll up the screen. Then, once it tries to bring up the Gnome login screen, I get a blank screen. BUT, I also hear the familiar bongos that accompany the login screen. My monitor reports the following: ```
1 D-SUB 
Out of Range
```

While the screen is still blank, I type my username and password in, and Breezy makes the magical sparkly login music that I'm used to hearing (still no video though). How can I configure my graphics card/monitor for Breezy if I can't get to a command line?

UPDATE: Here's some more info about my display settings from exporing through the Control Panel in XP:

Display Adapter: RADEON x300 Series
Screen Refresh Rate: 60Hz
Hardware Acceleration: Full
Display Resolution: 1600x1200

Thanks!

December 1 2005, UPDATE: I have solved this problem! I typed in the following:
```
sudo dpkg-reconfigure xserver-xorg
```

And then selected the 'vesa' driver....I stole this code from other posts, sorry I didn't bookmark them to give proper credit. My display resolution is still off, it's too big, but it's still quite useable.

---

