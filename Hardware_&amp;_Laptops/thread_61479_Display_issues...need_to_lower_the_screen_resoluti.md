---
title: "Display issues...need to lower the screen resolution"
date: 2005-08-31
forum: Hardware &amp; Laptops
---

### Post by LauraRey on 2005-08-31
I'm new to linux and have just installed ubuntu on my Dell Inspiron 5000E laptop.  Everything went well, except when I tried to change the display resolution to something lower than 1600 x 1200, the screen became a real mess.  

I've edited the /etc/x11/xorg.conf file to make sure that the resolutions I need are there.

Any other suggestions? 

thanks,
Laura

---

### Post by 5-HT on 2005-08-31
When you were trying to change the resolution, was that through system>preferences> screen resolution, or through editing xorg.conf ?

After I installed, my resolution was stuck on 1600x1200 and changing the resolution through the GUI didn't persist after rebooting, and I had to manualy delete any reference to a resolution that was higher than what I wanted in xorg.conf.

But as you mentioned the screen becomes a mess...so you may be experiencing something completely different (so maybe a res not supported?).

If changing the res through the GUI was ineffective, I'd suggest (if you haven't done so already) deleting (after making a back up just to be on the safe side) the references to any resolutions higher than what you'd like to use (x seems to like to use the highest available) in xorg.conf and see if a reboot after that helps out.

Then again I'm just starting out with ubuntu as well, so someone else may have a much better suggestion.

---

### Post by LauraRey on 2005-09-01
When I change the res through the system prefs, it just gets confused. The screen duplicates the right half and the flickering is bad.  I editted the xorg.conf file, but no change.

Thanks for your reply.

---

