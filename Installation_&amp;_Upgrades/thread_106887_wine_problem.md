---
title: "wine problem"
date: 2005-12-21
forum: Installation &amp; Upgrades
---

### Post by [pl]ice on 2005-12-21
hi, i'm trying to follow howto using dvd shrink/decryptor, i had no probs under hoary... but here it's a mess!
  installing wine (through apt) gives me set of directories, but none of them have the right structure!  : dosdevices  drive_c  system.reg  userdef.reg  user.reg
  in the howto i need to run winesetup, to get the folders correct/config files. but when i install winesetup (have to uninstall wine) the folders change to right thing, but i can't install programs couse i don't have wine then! shits me this thing!
pls help!

---

### Post by GregMartyn on 2005-12-21
Please post a link to the howto you are trying to follow.

Of course I also have to ask why you're not just using Linux software to do what you need. Have you tried dvd::rip? ([http://www.exit1.org/dvdrip/](http://www.exit1.org/dvdrip/)) Then you can use k3b to burn the DVD.

---

### Post by [pl]ice on 2005-12-21
[http://www.ubuntuforums.org/showthread.php?t=36112&highlight=dvd+decryptor](http://www.ubuntuforums.org/showthread.php?t=36112&highlight=dvd+decryptor)

yeh i just installed dvdrip, haven't used it yet. ...
  but that wine is really annoying, i can run dvd shrink, but the decryptor doesn't recognise my drives, i guess due to config in wine(i need to change that) but that's only in winesetup ... so it's a circle :)
thnx

---

### Post by dcstar on 2005-12-21
[QUOTE='[pl]ice']hi, i'm trying to follow howto using dvd shrink/decryptor, i had no probs under hoary... but here it's a mess!
  installing wine (through apt) gives me set of directories, but none of them have the right structure!  : dosdevices  drive_c  system.reg  userdef.reg  user.reg
  in the howto i need to run winesetup, to get the folders correct/config files. but when i install winesetup (have to uninstall wine) the folders change to right thing, but i can't install programs couse i don't have wine then! shits me this thing!
pls help![/QUOTE]

Install wine (via Synaptic), open a USER terminal and type "winecfg".

You should be able to set up your drives.

---

