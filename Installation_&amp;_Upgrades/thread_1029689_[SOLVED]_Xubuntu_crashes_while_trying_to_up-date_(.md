---
title: "[SOLVED] Xubuntu crashes while trying to up-date (8.10)"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by pancakewagon on 2009-01-03
I have Xubuntu installed through Wubi and i run the update program and when it gets about half way through the install, it crashes! I cant move my mouse cursor and i just have to reboot. After that i cant update because i get an error (from shutting down though the middle of the install) so I reinstalled Xubuntu and tried to up date again... same thing happens!!:confused: I'm new to Linux and Ubuntu  (windows Xp sp3, 450mhz 384mb of ram)

Also this seems to happen right as i get it out screen saver(black screen)

---

### Post by zvacet on 2009-01-03
Can you boot in recovery mode and run 

```
apt-get update && apt-get upgrade && apt-get dist-upgrade
```

---

### Post by pancakewagon on 2009-01-03
I'm in the middle of reinstalling it right now so when i get it installed I'll see if that works.

---

### Post by pancakewagon on 2009-01-03
oh... how do you boot in recovery mode?

---

### Post by zvacet on 2009-01-03
I never worked with Wubi so maybe my advice is not quite accurate.When you choose whitch OS you want to boot do you see Ubuntu kernels?If you do you should have recovery option there.

---

### Post by pancakewagon on 2009-01-03
I found this I'm going to see if it works :D 
[http://ubuntuforums.org/showthread.php?t=520737](http://ubuntuforums.org/showthread.php?t=520737)

---

### Post by pancakewagon on 2009-01-03
YAY! I got into recovery boot! I'm at the "Recovery Menu" options are, resume, clean, dpkg, fsck, root, xfix . What do i choose?

---

### Post by pancakewagon on 2009-01-03
nvm i figured it out! :D so im about to hit "y" to get the updates.

---

### Post by pancakewagon on 2009-01-03
Uh-Oh.... "Unable to fetch some archives, maybe run apt-get update or try with --fix-missing T-T

"edit" it can get the latest updates but it fails to download them! Idk whats wrong lol!!
"another edit" I figured it out! Well kinda... since i could not get it to work through the terminal in system recovery boot, i retried it in normal boot and except this time I didn't let the screen saver go on. And it didn't crash!!!

---

