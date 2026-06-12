---
title: "[SOLVED] Can't Install and Can't find"
date: 2008-08-26
forum: General Help
---

### Post by dphoenixa on 2008-08-26
I just install Xubuntu on my desktop and i've been tring to install automatix2 but it isn't working as it should. I am kinda lost and don't know what to do.

I also installed google earth and it said it was good, but I can't find it anywhere in the applications or anywhere in any of the files. 

This is what i did:
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install googleearth-4.3

---

### Post by overdrank on 2008-08-26
> **dphoenixa said:**
> I just install Xubuntu on my desktop and i've been tring to install automatix2 but it isn't working as it should. I am kinda lost and don't know what to do.

I also installed google earth and it said it was good, but I can't find it anywhere in the applications or anywhere in any of the files. 

This is what i did:
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install googleearth-4.3

Hi and automatix is not supported in the forums and we can help you install the apps you required.
Have you tried to run googleearth in the terminal or by using the alt, F2 keys. If you run in the terminal it will show you any errors.

---

### Post by mixmaster on 2008-08-26
You should read [this](https://help.ubuntu.com/community/Automatix) before considering installing/using automatix.  Basically it is not supported by the community, can cause problems and is no longer even supported by its author.

---

### Post by dphoenixa on 2008-08-26
I was able to work it out with google earth, and i decided against automatix. i had to input su then dpkg --configure -a and had to do the update manager and updated it and it worked.

thanks for your help though.

---

