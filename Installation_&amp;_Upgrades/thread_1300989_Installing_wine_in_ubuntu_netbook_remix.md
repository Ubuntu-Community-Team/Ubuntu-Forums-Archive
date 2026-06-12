---
title: "Installing wine in ubuntu netbook remix"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by warmo161 on 2009-10-25
Hi there, i have used usbuntu to make me a persistant usb version of netbook remix 9.04. but when running it in usbuntu, it treated the iso as ubuntu 9.10 RC2

when i have added the sources to install wine and added the key, the message comes up:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libopenal1 but it is not installable
        Recommends: ttf-mscorefonts-installer but it is not installable
E: Broken packages

---

### Post by Jbike on 2009-11-07
I have the same problem... exactly. I don't want to need it, but I have a single circuit simulation tool that is not availiable for linux. Seems to me that wine was included in ubuntu9.10, why not the netbook remix?

Jbike

---

### Post by Jbike on 2009-11-14
Solved my own problem. Just go to software sources, and add all the repos that come standard on Ubuntu 9.10. Wine will then be in synaptic. I installed it, and am now running my rogue program that I need. 

Jbike

---

