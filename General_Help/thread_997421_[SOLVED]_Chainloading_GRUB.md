---
title: "[SOLVED] Chainloading GRUB"
date: 2008-11-29
forum: General Help
---

### Post by 10nitro on 2008-11-29
I have just GRUB installed on /dev/sda1 (hd0,0)
I have Ubuntu and GRUB installed on /dev/sda9 (hd0,8)

I'm able to switch which one load by running
```
GRUB> root (hd0,*x*)
GRUB> setup (hd0)
```

However, I would like to have a menu option in each to chainload into the other.

---

### Post by plucky on 2008-11-30
Try a "configfile" boot in each of your menu.lst files should do what you want.

See this [grub link](http://users.bigpond.net.au/hermanzone/p15.htm#Second_method_configfile_boot) for setting up config file boot.


Good Luck

---

### Post by Elfy on 2008-11-30
I have intrepid installed on my sda hdd and I have jaunty installed on my sdc hdd - I have jaunty grub installed on sdc and the main intrepid grub installed on sda

In my menu list I call the jaunty grub like

> title           Jaunty Jackalope
root            (hd2)
chainloader	+1

So when I pick jaunty from my main menu I get the jaunty menu from which I can pick what boots.

---

