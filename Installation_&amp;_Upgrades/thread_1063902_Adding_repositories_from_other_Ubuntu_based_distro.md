---
title: "Adding repositories from other Ubuntu based distros."
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by casbahdk on 2009-02-08
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

I came across the above code from [www.linuxidentity.com](www.linuxidentity.com) for adding repositories from other based distros. How do I find repositories from other Ubuntu based distros to add to my sources.list? An example would be to try some of Linux Mint's GPL'd tools. Is there somewhere where other Ubuntu based distros like Linux Mint, #! crashbang linux, OzOS, gOS, etc. post where their repositories are located?

---

### Post by jaygo on 2009-03-11
I haven't round any such posts, but you can ask/search in their forums or install their OSes in virtualbox or run from a CD and just copy the repo's from there.

---

### Post by casbahdk on 2009-03-11
> **jaygo said:**
> I haven't round any such posts, but you can ask/search in their forums or install their OSes in virtualbox or run from a CD and just copy the repo's from there.

Thanks

---

### Post by Neo_The_User on 2009-03-11
You can avoid this problem by not changing sources.list to other distros. Install the other Ubuntu based distro from CD if you want them. Don't slowly migrate. ;)

DO NOT mix other repos with Ubuntu EXCEPT Medibuntu unless it is absolutely necessary and you just love problems.

---

### Post by avtolle on 2009-03-11
casbahdk, be aware that some repos, e.g., Linux Mint, will not have anything for ppc (your sig indicates you are running on a G5) as the distro has no ppc release.

---

### Post by Neo_The_User on 2009-03-11
> **avtolle said:**
> casbahdk, be aware that some repos, e.g., Linux Mint, will not have anything for ppc (your sig indicates you are running on a G5) as the distro has no ppc release.

Exactly.

---

### Post by casbahdk on 2009-03-11
> **avtolle said:**
> casbahdk, be aware that some repos, e.g., Linux Mint, will not have anything for ppc (your sig indicates you are running on a G5) as the distro has no ppc release.

Thanks for the heads-up. It would be cool to mix and match #! CRUNCHBANG Linux with Linux Mint as an example, but yes, I am aware of the problem. I was mainly interested in non-destructive stuff :-) like using the Blubuntu theme in Linux Mint (I have a Lenovo T60 as well). Sometimes it is useful to be able to grab a program that one or the other Ubuntu derivative doesn't have, but which another has.

---

### Post by avtolle on 2009-03-11
Missed the Lenovo in your sig. Mint does have some intresting themes, along with some "unique to Mint" apps. However, I think that one must be very careful with trying apps from other distros, or problems (minor to major) can occur. Good luck.

BTW, just thinking out loud; could not said theme be downloaded from Mint and placed in your 8.10 themes? I've never done this, but it seems it should be doable. Perhaps a Google search might help, or a Forum search here to see if there exists any threads where this has been done.

---

