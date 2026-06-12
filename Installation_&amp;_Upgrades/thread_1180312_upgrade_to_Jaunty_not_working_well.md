---
title: "upgrade to Jaunty not working well"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2009-06-06
After I upgraded to Jaunty I cannot open a terminal (Applications>terminal) and some other problems (sound, networking) cropped up as well.  My windows are no longer set up the way they used to be, for one thing, and the fonts at login are small and hard to read.

Whenever I use update manager I'm greeted with a message box "Not all updates can be installed" and "This can be cause by: A previous upgrade which didn't complete...etc."

Don't know where to begin.  Should I just start over and burn an ISO image of Jaunty and go from there?  If so, can I keep my hard drive partitions the same or do I have to re-partition everything?

Any and all suggestions would be greatly appreciated.

---

### Post by CJ_Hudson on 2009-06-06
I think there is another way of opening the terminal window maybe using a control-key keyboard shortcut?
Then you could use

sudo get update
sudo apt-get update

I'm a bit out of practice though so better check those commands.
Sorry I can't be more helpful.

---

### Post by merlinus on 2009-06-06
FWIW, I have always had better luck with an install vs. upgrade.  Also, I can then testdrive the new version from the live cd to see if there will be problems (e.g. graphics, sound, wireless).

If you d/l the .iso and use it to install, then you can certainly keep your partitions, and the data if you do not format them.  

I have even read somewhere that Jaunty will give you the option of not formatting /, so that everything in /home stays intact but all system files are reinstalled.

---

### Post by raymondvillain on 2009-06-06
Thanks, Merlinus.  That looks promising.  I'll try it and hope for the best.

---

