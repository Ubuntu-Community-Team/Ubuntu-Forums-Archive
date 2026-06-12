---
title: "Installing from source breaks dpkg?"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by ebin on 2009-03-04
I needed to install numpy and matplotlib from source at one point, and then recently installed emacs22.3 from source, and now when I use apt-get or anything else that uses dpkg I have a bunch of dependency errors and configuration errors.

The biggest error I made was in trying to purge my system of emacs I deleted many things with the name emacs in it, this aided in confusing dpkg.

Commands such as 
# dpkg --configure -a
# apt-get install -f
etc give the same error. 

I have also tried rebooting and running the dpkg fix broken packages from "safe mode"

Has anyone else made the same dumb mistake as I did (in mass deleting an application installed by dpkg?) and does anyone know how to repair this issue (short of re-installation)

Thanks

---

