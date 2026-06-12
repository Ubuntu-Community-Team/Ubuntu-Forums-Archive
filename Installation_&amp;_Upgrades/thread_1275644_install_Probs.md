---
title: "install_Probs"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by navaneethan on 2009-09-26
I have downloaded many packages like vlc,erlang,openjdk..to install in my hardy

but it does't support to install 

"I need to know that how to find which kind of package support to my system or my hardy" then only i can download those packages to install offline in my hardy


[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif) Cool with hardy

---

### Post by rreese6 on 2009-09-26
are you downloading packages the end in .deb?
or are they source files ending in tar.gz or tar.bz2 etc?
if they are .deb, make sure they are for hardy
and then use dpkg -i <name>.deb
for example
dpkg -i vlc-2.4_386.deb

---

