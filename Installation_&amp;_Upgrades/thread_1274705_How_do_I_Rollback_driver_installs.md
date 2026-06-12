---
title: "How do I Rollback driver installs?"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by jessiebrownjr on 2009-09-24
If I download the new Xorg driver for my laptop.. again... and it crashes.. again... how do I roll back the driver? Im assuming I have to options.. command line, and safe mode (maybe) to fix it... Anybody mind shedding some light on this for me, or referencing me to a site doing this? Ive tried the search, yields too many non useful links :-)


Thanks in advance!

---

### Post by jessiebrownjr on 2009-09-25
Shameless self bump, help :-):confused:

---

### Post by earthpigg on 2009-09-25
do you know the package name of what you installed, and the package name of what you had installed previously when things where working?

can you clarify this, please:

> and it crashes

(that obscurity is probably why no one previously offered to help you.... the more details you provide, the more likely you are to have folks rushing to your aid.

exact error messages are great. if its a boot-time error and you cant take a screen shot or copy/paste, then take a picture with a digital camera and upload it.

try to anticipate any possible question anyone wishing to help may have, and include it in your posts.)

---

### Post by jessiebrownjr on 2009-09-26
> **earthpigg said:**
> do you know the package name of what you installed, and the package name of what you had installed previously when things where working?

can you clarify this, please:



(that obscurity is probably why no one previously offered to help you.... the more details you provide, the more likely you are to have folks rushing to your aid.

exact error messages are great. if its a boot-time error and you cant take a screen shot or copy/paste, then take a picture with a digital camera and upload it.

try to anticipate any possible question anyone wishing to help may have, and include it in your posts.)

thanks for the reply! 

The update is the Xorg driver update from the synpaptics.. i have an intel card, and the last I read it was a known bug.  But what Im trying to learn is how to fix this situation.. no matter what driver, no matter what happens.. What would I do?

---

### Post by jessiebrownjr on 2009-09-27
seems that wasn't why I gots no reply :-)

---

### Post by earthpigg on 2009-09-27
go here, and look at the .deb files. if you haven't run apt-get clean recently, the old .deb file may still be there.

/var/cache/apt/archives/

---

### Post by jessiebrownjr on 2009-09-28
> **earthpigg said:**
> go here, and look at the .deb files. if you haven't run apt-get clean recently, the old .deb file may still be there.

/var/cache/apt/archives/

The crash I'm referring to is incompatible driver/hardware and it fails to display anything.. Its been a long week I guess so I forgot exactly what it looks like but it seems to be a common issue.  It would start to boot but when normally im assuming x/gnome starts, nothing shows up, just a blank/greenish black screen shows up... Now, I haven't felt like recreating this to show you exactly sense I don't know how to fix it.. 

I found the directory you were talking about, its choc-full of various crapola..  But now what do I do with it etc?

---

