---
title: "uninstalling driver"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by Hansje on 2007-02-20
I am trying to install nvidia's video driver in my linux. (Ubuntu Edgy Eft). Eech time it goes wrong, i downloaded the driver from nvidia (NVIDIA-Linux-x86-1.0-9746-pkg1.run). Installed it with sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run. It worked for me only once: after installing it succesfull i needed to edit some files in windows (needed write support for NTFS). after that i restart in ubuntu and my screen remains black. Its not a crash because i hear the sound that indicates that i can typ my username, but screen is still black. Setting my xorg.conf back won't help. 
I reinstalled linux, tried to install the driver, but no good, this time he gives me a warning, its a shame that i forgot to wriht it down... it had something to do with guessing the location of some things. He advised me to work in another level... also i had to install X.org, pkg.config SDK/development . 
This is the third time that i reinstalled, but it won't work, my question is: how do i remove the driver? and how do i install it properly so i can still boot in windows without making the linux driver to stop working properly?

Hope someone can help me.

Greetz
Hansje

---

### Post by Hansje on 2007-02-20
It solved already, i found out what the problem was, there is a secondary monitor connected to my laptop, but its switched off. After installing the driver the login display is at the secondary screen and my laptop screen remains black. I solved it by disconnecting the secondary screen and reinstalling the driver. 
But why is the screen comming up at the secondary monitor? is there a reason for this?

Greetz
Hansje

---

