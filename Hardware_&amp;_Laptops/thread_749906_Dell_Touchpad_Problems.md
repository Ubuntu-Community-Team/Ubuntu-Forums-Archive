---
title: "Dell Touchpad Problems"
date: 2008-04-08
forum: Hardware &amp; Laptops
---

### Post by jorwex on 2008-04-08
Hey all,

my cousin brought his dell laptop inspiron 6000 down this weekend and we redid his ubuntu installation. once we got everything up and running he told me that since his switch from windows, the only thing that's been bugging him was that his touchpad sensitivity doesn't change if he changes it in Mouse in the administration/preferences menu. he said in windows he could fling the cursor across the screen but he can't do the same if he changes the sensitivity in linux.

so i did some searching and installed GSynaptics and I added that line in xorg.conf
I changed the sensitivity with that and it didn't change anything either. I read a bit more and found out that the touchpad sometimes doesn't get detected correctly in xorg, but i checked and it was fine. I also went to Gsynaptics website and it said you had to add a startup command in Sessions, but I noticed that there was already a GSynaptics entry, so I just changed it to what the site said it should be ("gsynaptics-init on").

anywho, still no luck. I havent tried QSynaptics, but it sounds like it targets the same thing. Any one got any advise?

---

### Post by chewearn on 2008-04-09
How about this:
[http://ubuntuforums.org/showthread.php?t=748596](http://ubuntuforums.org/showthread.php?t=748596)

---

