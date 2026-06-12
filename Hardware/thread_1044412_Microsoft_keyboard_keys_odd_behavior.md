---
title: "Microsoft keyboard keys odd behavior"
date: 2009-01-19
forum: Hardware
---

### Post by Hooya on 2009-01-19
After my ugrade to 8.10 I found my multimedia keys didn't function correctly on my Microsoft Natural Multimedia Keyboard 1.0A.

xev reports mis-bindings of the keys.  For instance, the "media" key reports XF86Back (which shouldn't be on the keyboard at all) and the Stop key reports XF86AudioLowerVolume.

The keys also seem to not want to bind properly with Amarok.  The Global Shortcuts section of Amarok doesn't want to respond to the multimedia keys unless the app has focus.  This didn't happen before the upgrade.

Is there a way I can totally reset the keboard settings to system default - what the system originally recognized?

I may have conflicts as I have ubuntu-desktop and kubuntu-desktop both installed on this system.  What app should I use (I do NOT want to use Keytouch) to get the keys reporting propertly?

Edit:  I should learn how to search better.  Found a solution here:
[http://ubuntuforums.org/showpost.php?p=6327383&postcount=4](http://ubuntuforums.org/showpost.php?p=6327383&postcount=4)

This also solves the Amarok issue, global shortcuts work all the time now.

---

### Post by Hooya on 2009-01-19
Trying to mark this as solved....

---

