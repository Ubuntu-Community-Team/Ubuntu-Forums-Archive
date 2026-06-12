---
title: "installing new kernel - which parts are neccesary?"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by KhaaL on 2009-02-22
I'm thinking about installing and trying out the new 2.6.29 kernel in 8.10, but since i'm a kernel newbie i have no idea what the different parts are for. looking at [the PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc5/"), what do i need besides the image (thats right for my architecture)? what are the linux headers needed for? And will my nvidia driver that i downloaded through synaptic (nvidia-glx-180) be required to be recompiled? also, what are these packages for:
linux-restricted-modules
linux-backports-modules

---

### Post by unrevealed01 on 2009-02-23
Open a Terminal from the menu Applications->Accessories->Terminal and type:

sudo apt-get update
sudo apt-get upgrade

then move on installing the drivers

it might take some time for you to figure out how to compile but don't get yourself in pressure just relax surf the net for tutorials. if you can't find out how to compile? just ask again who knows the answer might pop up

---

### Post by KhaaL on 2009-02-23
i appriciate your help, but as stated in my previous post i was not intrested in the kernel provided through the repos but rather the shiny new .29 series and how my current drivers are affected - if they would require recompilation or not since i read that a new feature in ubuntu would save the user from recompiling modules with every new kernel upgrade...

---

