---
title: "Installing ubuntu on unsupported raid card rockreaid 2320"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by supperman2k on 2009-04-24
I have an 8 port sata controller that doesnt have drivers available with the installation cd, however I checked their site and they have an open source set of drivers that will be required to compile.

How do I install Ubuntu onto the raid array that I have created via the controller?

The raid controller in question is a highpoint rocketraid 2320, and I would like to install ubuntu 8.04

---

### Post by tgrimley on 2009-09-10
Compile them on another system targeted to the same kernel version, add them (the *.ko) to the boot direction on the driver install disk, and follow the directions supplied in the install pdf...

would be my guess.

You ever get this to work?

---

