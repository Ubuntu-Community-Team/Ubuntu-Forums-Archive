---
title: "Virtualbox 3d acceleration"
date: 2008-04-09
forum: Hardware &amp; Laptops
---

### Post by jeffhollon on 2008-04-09
my video card in my laptop has a 3d card in it.  I am just wondering if there is a way to enable the full power for virtualbox instead of just 2d??????????

thanks,

Jeff

---

### Post by pytheas22 on 2008-04-09
As far as I know, VirtualBox still doesn't support 3d acceleration.  I think it's being planned but it's not out yet.  I do remember reading that there's software that will allow you to run applications requiring 3d acceleration inside a VirtualBox virtual machine, but only if the application uses OpenGL.  I'm guessing that you're looking to run DirectX games on a virtual Windows system, so this won't help you.  However if you are interested in the OpenGL stuff, I can try to find the link where I read about it.

Also, vmware does have beta support for 3d acceleration in virtual machines, at least in principle--I've never gotten it to actually work, and not for lack of trying.  But if you want to explore that route, you can install vmware player for free through Synaptic, although it requires some work to get Windows installed without the commercial version of vmware.

---

