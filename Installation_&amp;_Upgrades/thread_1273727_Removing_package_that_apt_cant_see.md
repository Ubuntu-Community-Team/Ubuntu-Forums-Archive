---
title: "Removing package that apt cant see"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by Red_Kaos on 2009-09-23
i was unable to find this problem anywhere in the forums so... 
how do i manually remove a program that apt doesn't show as being installed?
i had previously done a manual install of an older version of wine because the newer version did not allow me to run EVE Online, but had begun updating it again after the problem was fixed. but when the latest dist upgrade came around it broke, for some reason winegl no longer exits even after a reinstall of wine . after uninstalling wine in adept i still get this

sean@Erubus:~$ wine --version
wine-1.1.26-233-gd65a391

and wine still runs... 

after  i install wine 1.1.29 it still gives me the same message. so what do i to completly remove it and start over?

---

### Post by Bachstelze on 2009-09-23
When you say "manual install", do you mean you compiled it from source? If so, there is no simple way to uninstall it, you must delete all the files it installed one by one.

---

### Post by Red_Kaos on 2009-09-23
i may have tried both manual and a .deb file... if so can i look in the deb file to see where the files go to? and why does kubuntu try to use the older version regaurdless of which one i have installed

---

