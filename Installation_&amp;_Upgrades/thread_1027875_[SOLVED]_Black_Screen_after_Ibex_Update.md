---
title: "[SOLVED] Black Screen after Ibex Update"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by hissing_sunhat on 2009-01-01
Hello,

I recently updated to 8.10 from 8.04 using the update manager. The splash screen and files needed to boot load no problem, but I never get to the login screen. Instead, my screen turns black. I can't get a terminal with cntrl-alt-F1 and the same thing happens in recovery mode. I checked my xorg.conf and there doesn't seem to be anything wrong with it. Passing boot options vga=771 noapic nolapic does not help. Can someone please help me? Thanks!

Dell Inspiron 1501
AMD Turion 64 Mobile
ATI Radeon Xpress 1150

---

### Post by abn91c on 2009-01-01
it may be the same problems a lot of user are having with compiz and desktop effects. if you cant log in at all removing compiz may help

---

### Post by hissing_sunhat on 2009-01-02
Hm, really? I'm just concerned because I can't even get a terminal. How would I go about disabling Compiz without one? Thanks for your help, I really appreciate it.

---

### Post by hissing_sunhat on 2009-01-02
Ok, so I just figured out the problem using abn91c's suggestion and someone's help from a different thread. Unfortunately, I can't remember which one it was. Here's how I solved my black screen problem

At the GRUB menu, press 'e' while selecting recovery mode.
Add the following to the end of the "kernel" line:
```
vga=771
```
Get a root terminal and enter the following
```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit

```

run xfix

I was then able to get a login screen and activate the restricted drivers. It seems like this problem many people are having has to do with compiz. So just get rid of it and use synaptic to get it again if you want.

---

