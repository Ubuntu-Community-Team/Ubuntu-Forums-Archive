---
title: "Dell M1530 - NVIDIA M8600M GT"
date: 2008-07-24
forum: Hardware
---

### Post by simonpearson on 2008-07-24
Hi Guys,

I've installed Hardy Heron using VirtualBox, and I wanted to share my experience with you, and also ask for some help.

*** My system is a Dell M1530 XPS that has an NVIDIA 8600m GT graphics card ***

[LIST=1]
[*]After installing Hardy, I noticed that "System > Administraion > Hardware Drivers" was showing 'No proprietary drivers are in use on this system'.

[*]Guessing I need to install the drivers I went to the NVIDIA web site, and tried to select my model - there were no entries for the 8600M GT, but there was an 8700M GT for Linux, so I downloaded these drivers (173.14.05).

[*]After running "sudo sh NVIDIA-Linux-x86-173.14.05.pkg1.run" I received the error:

> WARNING:
You do not appear to have an NVIDIA GPU supported by the 173.14.05 NVIDIA Linux graphics driver installed in this system.  For further details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com)

[*]I dropped back to Windows, went to the NVIDIA web site and ran the probe tool to establish what drivers it thought I should use.  Only to be told : "Dell requires that you download the driver for your GPU from their support site."

[*]As DELL didn't have these on their web site either, I called DELL...... And got told by tech support there were no (nvidia) drivers for (linux on) my laptop.

[*]I googled for a bit to no avail.. but admitedly not extensively.[/LIST]


So now I'm running out of ideas - can anyone help?! :)

</Simon>

---

### Post by nuschii on 2008-07-26
> **simonpearson said:**
> Hi Guys,

I've installed Hardy Heron using VirtualBox, and I wanted to share my experience with you, and also ask for some help.

*** My system is a Dell M1530 XPS that has an NVIDIA 8600m GT graphics card ***

[LIST=1]
[*]After installing Hardy, I noticed that "System > Administraion > Hardware Drivers" was showing 'No proprietary drivers are in use on this system'.
[/LIST]


Well, graphics acceleration is simply not possible in VirtualBox - or any other virtualization software I know of. I guess this would just be too complicated to implement. So VirtualBox provides some standard VESA graphics adapter to the guest OS, and that's it.

If you want to have graphics acceleration in Ubuntu, you will have to install it as a "real" OS on your hard drive. As I own the XPS M1530 myself, I can asure you it works great on this machine.:) Despite of some touchpad issue, which is resolved in another thread in this forum.

Have fun!

nuschii

---

