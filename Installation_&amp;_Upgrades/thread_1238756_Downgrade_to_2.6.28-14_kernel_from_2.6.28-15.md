---
title: "Downgrade to 2.6.28-14 kernel from 2.6.28-15"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by jaffa_nz on 2009-08-12
Kia Ora team.

I've searched and am unable to find a simple step method to add kernel version "2.6.28-14" to my Ubuntu 9.04 2.6.28-15 install. (Dell D620 laptop)

When i search for 2.6.28-14 in Synaptic it doesn't show up.

I had both previously installed, as i'd gone through from an earlier kernel 9.04 etc.  I found that the -15 kernel was buggy and froze up heaps, so i was running -14 previously.  Yesterday i had to rebuild, of course the update took me to 2.6.28-15 and now i want to run -14 again to see if the freezes stop.

All assistance greatly appreciated. cheers

---

### Post by philcamlin on 2009-08-12
the kernels are saved anyways :)
just select them from the grub menu when you boot the computer up you should see the option to click the -14 kernel

---

### Post by pizza-is-good on 2009-08-12
If the output of
```
update-grub
```
says that you still have 14 installed, then
```
gksu gedit /boot/grub/menu.lst
```
and change one of the entries to all 14 instead of 15. 
Details on that on [http://ubuntuforums.org/showthread.php?t=1231494](http://ubuntuforums.org/showthread.php?t=1231494)
go down to post #6.
 
Hope that helps.

---

### Post by jaffa_nz on 2009-08-12
Kia Ora.

Actually that advise was also something i was after so thanks heaps.  Especially the grub-install which will always be useful!

Unfortunately on my clean laptop I don't have anything other than -11 and the -15 kernels.

Which synaptic entries do i need to search for and select to Install (2.6.28-14).  Now I also understand that the GRUB should be updated appropriately after i install them..

cheers

---

