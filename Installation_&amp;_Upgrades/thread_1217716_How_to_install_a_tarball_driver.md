---
title: "How to install a tarball driver"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by cooper77z on 2009-07-19
I did a search on "how to install a tarball" but I got nothing. Can somebody please teach me how to install a tarball driver?

---

### Post by Partyboi2 on 2009-07-19
Hi, a tarball is a a tar archive  and needs to be extracted. You can either do this by right clicking on the tar and choosing to extract or you can extract them using the terminal. 
Normally the tarball's end with 2 types of file extensions, either the .tar.gz or tar.bz2 so if you have a filename.tar.gz, you would use this command in the terminal
```
tar xvzf filename.tar.gz
```
if you had a filename.tar.bz2, you would use
```
tar xvjf filename.tar.bz2
``` Once you have extracted it you can follow [[COLOR=Blue]this[/COLOR]]("http://www.tuxfiles.org/linuxhelp/softinstall.html") though if it has a configure file, it does not not have a configure file in the source directory have a look for a INSTALL file as this nornally tells you how you can install it. 
Any problems let us know what the name of the software you are trying to install and where you are getting stuck.

---

### Post by cooper77z on 2009-07-20
I am pretty sure the drivers for easycap are installed but I think the devrec install failed. Cinelerra knows the easycap hardware exists but it trys to capture the video in component format, which the format is composite.

---

