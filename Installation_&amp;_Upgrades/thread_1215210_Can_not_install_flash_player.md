---
title: "Can not install flash player"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by Masako on 2009-07-16
Hey guys, I just completed a fresh install of ubuntu using wubi. When I tried the disc preview flash worked but noow when I try to install flash this error comes up:
 [IMG]http://i301.photobucket.com/albums/nn64/yoyoyo1310/Screenshot.png[/IMG]


Any ideas?

---

### Post by starcraft.man on 2009-07-16
Don't install flash via a deb, not recommended. I believe the architecture comment comes up because you install an x64 system and are now installing an i386 package without the wrapper for computability. To save the hassled, I'd recommend you just install the ubuntu-restricted-extras package.

Open a terminal (applications > accessories > terminal) then type in and return:

```
sudo apt-get install ubuntu-rectricted-extras
```

That will install flash, video codecs, java, and a bunch of other packages you'll likely need. Shouldn't be a problem once all finished. For more info on installing programs in Ubuntu, see my sig section.

---

### Post by Masako on 2009-07-16
Thanks alot man.

---

### Post by Masako on 2009-07-17
Unfortunatly I got this error E: Couldn't find package ubuntu-rectricted-extras

---

### Post by izizzle on 2009-07-17
Run "sudo apt-get update" then run "sudo apt-get install ubuntu-restricted-extras"

---

