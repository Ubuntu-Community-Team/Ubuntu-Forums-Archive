---
title: "installing linux-image-2.6.27-7-generic"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by banter25 on 2009-01-05
Every time I try to install the above mentioned package on Hardy Heron, I keep getting the following error

E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_amd64.deb: subprocess pre-installation script returned error exit status 1

What do I do to fix this????  It's got me floored.:confused:

---

### Post by 2hot6ft2 on 2009-01-05
> **banter25 said:**
> Every time I try to install the above mentioned package on Hardy Heron, I keep getting the following error

E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_amd64.deb: subprocess pre-installation script returned error exit status 1

What do I do to fix this????  It's got me floored.:confused:
Don't know if you can get it in Hardy or not. I have it in Intrepid.
That don't even look right. Took it out

---

### Post by lswb on 2009-01-05
May be related to hardy using the 2.6.24 kernel rather than 2.6.27. How are you attempting to install? dpkg or did you add intrepid repository to your hardy sources.list or ?

---

### Post by banter25 on 2009-01-05
used dpkg and when i try the sudo apt-get install thread of commands i get the following error 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.27-7-generic_2.6.27-7.16_amd64


acts like everything was going fine then throws that out

---

### Post by lswb on 2009-01-05
If you are certain that you want to experiment with a different kernel version, than the one that hardy normally uses, you will need to also install a matching module directory tree and whatever other dependencies are required for that kernel to run. Probably the easiest way to do this is to temporarily add the intrepid repositories to /etc/apt/sources.list. Do the apt-get of the kernel then change your sources.list back to the original. DO NOT DO ANY OTHER UPDATES WHILE YOU HAVE THE INTREPID REPOSITORIES IN YOUR HARDY sources.list FILE!

Good Luck!

---

