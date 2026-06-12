---
title: "Last Update makes black screen"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by yellowbosch on 2009-01-06
hi all,
today after a normal update, after restart, when it boots, the session screen turns black but working!
i can write the login and pass, but nothing appears!

i have a LG laptop, with 8.04 LTS upgraded to 8.10, and i was using fluxbox...so i choose gnome to make updates to the system...and after that it turned black!

thanks,
ricardo

---

### Post by lemming465 on 2009-01-19
There are some video issues with initial intrepid installs, which can usually be fixed with patching, or by switching to a different video driver (e.g. "nv" or "vesa" instead of "nvidia"). Nvidia, ATI, and Intel chips of various vintages have glitches, so this hits lots of people, e.g. me.  Boot the single-user "rescue mode" and try ```
/etc/init.d/networking start
apt-get update
apt-get upgrade
dpkg-reconfigure xserver-xorg
```

---

