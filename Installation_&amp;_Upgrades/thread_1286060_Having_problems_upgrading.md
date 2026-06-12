---
title: "Having problems upgrading"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by banquo on 2009-10-08
hello!
I'm having problems with upgrading my 8.04 ubuntu.
I've got all the latest updates in the (graphic) update manager, but can't see
the 'upgrade ubuntu"bar/button.
I've tried "sudo apt-get dist-upgrade" and "sudo apt-get upgrade" in terminal as well, with
following output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I've tried 

gksudo "update-manager -c"
as well, but still can't find newer version of ubuntu.

I hope some1 out there can help me :$   thanks =)

---

### Post by Daniel1994 on 2009-10-08
Have you tried Alt+F2 and then "update-manager -d"?

---

### Post by jeremyswalker on 2009-10-08
Did you try:
```
sudo update-manager -d
```

---

### Post by banquo on 2009-10-08
nice, it worked :) thanks guys..
after tryin meta+F2 -c , then adviced trying -d instead i was afraid
of having to try the whole alphabet ;)

---

