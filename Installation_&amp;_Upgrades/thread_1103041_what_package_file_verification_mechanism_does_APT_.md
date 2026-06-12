---
title: "what package file verification mechanism does APT use, if any?"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by arsmith on 2009-03-22
I have two computers, and i just updated one of them.  I'm trying to save myself from having to download all of the updated package files a second time, so i just snuck all the .deb's out of /var/cache/apt/archive on the already updated computer.  I have reason to believe that some of them might not have copied over completely.  What I want to know is whether or not synaptic'll try to verify package files before installing them.  I know that itll recognize ones that are already in that directory and not download them.  If not, I have checksums of every .deb, maybe it would be possible to create a script to traverse my list of checksums and then google each individual checksum and return a failure exit status if the results page contains the string "did not match any documents."  Not sure how to go about this, maybe use lynx?  Obviously, none of this is necessary if it turns out that synaptic verifies the packages itself.

---

### Post by Pumalite on 2009-03-22
You can make a script in Synaptic or use AptOnCD:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by arsmith on 2009-03-22
what do you mean? how exactly would you use the build download script feature of synaptic to *verify* packages?

---

