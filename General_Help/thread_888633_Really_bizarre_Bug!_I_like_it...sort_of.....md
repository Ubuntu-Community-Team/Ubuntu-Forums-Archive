---
title: "Really bizarre Bug! I like it...sort of...."
date: 2008-08-13
forum: General Help
---

### Post by davidpeace on 2008-08-13
I was using instructions from a book, Beginning Ubuntu Linux, to put the trashcan icon on the desktop. I opened up a terminal, typed "gconf-editor", no quotes and no sudo. I clicked apps, scrolled down to Nautilus, clicked and then selected Desktop. On the right side were options. One of them was to make the trashcan icon visible. I clicked it and that's when the weird thing happened. When I first set up my cube, I loaded several images but only ever got one, for all the desktops. But after clicking the above checkbox, I suddenly had different wallpaper for each desktop. Unfortunately, it didn't stick with a reboot. But it was repeatable. To get the different wallpapers, I go to gconf-editor and repeat the above process. Unfortunately, the trash icon did not show up on the desktop at any time.:(

What makes this more bizarre is that I have the same setup on a different partition that I use for experimenting on. I did the same thing here, but only the one wallpaper on all the desktops and the trashcan icon **did** show up. I looked in the system monitor, messages, daemon,... but I couldn't see anything I could recognize that might have caused this. The only other thing I did was uninstall the Ubuntu repository version of Seamonkey (1.1.9) and manually install Seamonkey 1.1.11 and set apparmor to restrictive for everything.

Has anyone got an idea of what actually happened, how I can make the change stick and still get the trashcan icon on my desktop?

Caution: the book states that gconf-editor gives the user a lot of power to change things but doesn't give any warnings if one is doing something disastrous. (Shouldn't there be a requirement for root, then?) So, be careful if you plan to experiment.

Thanks for any help, in advance.

---

### Post by davidpeace on 2008-08-15
bump

---

