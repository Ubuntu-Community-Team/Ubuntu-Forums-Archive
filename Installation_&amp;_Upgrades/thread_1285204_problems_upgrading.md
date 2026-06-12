---
title: "problems upgrading"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by banquo on 2009-10-07
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

I hope some1 out there can help me :$   thanks =)

---

### Post by wojox on 2009-10-07
Try Alt+F2

And enter:

```
gksudo "update-manager -c"
```

---

### Post by banquo on 2009-10-07
thanks, I tried that, and I got some updates, mostly on open office, but no upgrading to the new ubuntu version, and I tried rebooting my computer, but when i run t update manager again ( with the command provided) it just says "your system is upp to date (.....)"

are there other ways,something elsse i could try? =)

---

