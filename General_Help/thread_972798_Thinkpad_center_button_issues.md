---
title: "Thinkpad center button issues"
date: 2008-11-06
forum: General Help
---

### Post by Dragutin on 2008-11-06
I have a thinkpad t42, just installed ubuntu 8 on it.  My thinkpad has a center mouse button right above the track pad, which is used to scroll (hold it down then move the red dot).  In previous versions, i could edit xorg.conf to make it act like a scroll wheel, but in this version my xorg.conf cuts off after the display section, so there is no mouse/keyboard/anything else.  Should i copy an old xorg.conf and replace this? or is there a new feature that I could use to configure this third button.  Thanks!

---

### Post by David_G_D on 2008-11-16
Hi,
I had the same issue when upgrading to 8.10 on my Thinkpad X22.

I followed the instructions at the very bottom of this page:

[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Scrolling](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Scrolling)

Now it works.

ACPI doesn't work well on my machine, so I use APM, and scrolling with the middle button no longer works after resuming from sleep!  I bet this won't be a problem for you if you use ACPI, but I would be interested to hear your results either way.

EDIT:

Oops!  I see the issue after suspend-resume is already being discussed here:

[http://ubuntuforums.org/showpost.php?p=6093137&postcount=13](http://ubuntuforums.org/showpost.php?p=6093137&postcount=13)

No solutions yet, though.

---

