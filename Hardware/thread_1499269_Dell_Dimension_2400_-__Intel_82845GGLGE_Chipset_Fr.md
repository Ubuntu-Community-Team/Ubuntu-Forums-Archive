---
title: "Dell Dimension 2400 -  Intel 82845G/GL/GE Chipset Freeze"
date: 2010-06-01
forum: Hardware
---

### Post by digitalcircuit36939 on 2010-06-01
I've got a Dell Dimension 2400 with the integrated Intel graphics card [Intel 82845G/GL/GE Chipset], and it freezes within 30 minutes of normal usage.  I've tried **every** workaround I've come across, and nothing has worked.
[LIST]
[*]Re-enabled KMS
[*]Upgraded Intel drivers to Glasen's PPA ([https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver))
[*]Downgraded drivers using X-Retro PPA ([https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-retro](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-retro))
[*]Installed Glasen's Intel 855GM patch ([https://launchpad.net/~glasen/+archive/855gm-fix](https://launchpad.net/~glasen/+archive/855gm-fix))
[*]Upgraded the kernel to latest RC version ([http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/))
[*]Downgraded to Jaunty kernel ([http://packages.ubuntu.com/jaunty-updates/linux-image-2.6.28-18-generic](http://packages.ubuntu.com/jaunty-updates/linux-image-2.6.28-18-generic))
[*]Disabled DRI
[*]Enabled UXA rendering
[*]Switched to vesa driver (worked, but I could not get a resolution above 640x480)
[/LIST]

I'm using Lucid Lynx with all updates installed.  Karmic Koala also repeatedly froze up, but Jaunty Jackalope worked fine.  From what I've researched, switching to another graphics card would work?  If I can't get this working in a few days, I'll have to move my Mom's user account to Windows XP.
Anything else that I can do?

---

### Post by sasaenator on 2010-06-02
Mainline kernels worked for me.I have the same graphic card,probably the easiest,but not the cheapest,way is to change the graphics.Maybe you can try the newest mainline kernel,I installed it today and looks like everything works.On the other hand your problem is not only the Intel graphic card.Hope you will find solution.7

---

