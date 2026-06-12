---
title: "script for tweaking RAM"
date: 2010-01-15
forum: Hardware
---

### Post by d3v1150m471c on 2010-01-15
I altered this script to so everyone on newer versions of ubuntu can use it. It should have read and write permissions to change it to your liking. **do not use this if you have less than 1gb of ram...** I encourage anyone who uses it to read the script. A: to learn what exactly it does and B: know that i'm not making something malicious on your system.

1. Extract the file and save it to your home folder.
2. Create a custom application launcher in your panel and name it utweak.
3. Set the command for the application launcher to:
gnome-terminal -e ./utweak
4. Click to run utweak.
5. Enjoy.

I encourage you to play around with this.... cache pressure and swappiness can be 0-100.
The less cache pressure, the more aggressively your computer will store data in your Ram so it can access it faster. The less swappiness, the more your system will rely on its Ram and less on the swap space. This is good because Ram is much faster than your hard drive's swap space when accessing information. I left it at 10 because your does need computer swap space. Especially for stuff like hibernating and the like.

**This will not make any permenant alterations to your system.**

---

