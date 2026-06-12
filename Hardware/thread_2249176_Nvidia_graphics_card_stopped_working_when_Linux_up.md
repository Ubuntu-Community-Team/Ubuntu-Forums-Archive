---
title: "Nvidia graphics card stopped working when Linux upgraded from 3.5 to 3.13"
date: 2014-10-20
forum: Hardware
---

### Post by evilbrent on 2014-10-20
I rebooted after a Linux update a while ago and I wasn't really paying attention to the implications of a message like "Nvidia no longer provide a driver for your graphics card" and I was like "Yeah, ok" and just clicked through. I didn't realise that really meant "Linux has decided that you don't need to use your monitor anymore."

I've been working around the problem by just booting to previous versions, but I'm ready to start having my Flash up to date etc....

Can anyone help me actually have the latest version of Linux recognised by my computer?

```
brent@Martha:~$ lspci
....
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
...

```

```
brent@Martha:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.5 LTS
Release:	12.04
Codename:	precise

```

---

### Post by grahammechanical on 2014-10-20
Actually it is not Linux that no longer provides the video driver for your card but Nvidia that no longer supports that Nvidia video card. There is a driver in Linux. It is open source and for Nvidia graphic adapters it is called Nouveau.

Did the OS reboot successfully after the upgrade from 12.04.4 to 12.04.5? Are you at a working desktop? Go to the Details page of System Settings and tell us what it says about Graphics. If it says Gallium 0.4, then you are running on Nouveau and you have the same version of Nouveau as I do and I am using Ubuntu 14.10.

Flash is nothing to do with the video driver. If you are using Firefox, then it is still possible to install the flash plugin installer. It is in the Software Centre. If you are using Chromium, as I am, then installing Flash will not get video working in Chromium any more and that is because of a decision by Google and not by the Linux developers. In this case we have to install Pepper Flash. It maybe in the 12.04 Software Centre. I do not know as I don't use 12.04. Look for Pepper Flash or pepperflashplugin.

Also, you may find an older Nvidia video driver in the Software Centre which can be installed. The Ubuntu Additional Drivers utility provides a small selection of the latest stable proprietary video drivers and not a complete selection of every driver that ever was.

Regards.

---

### Post by evilbrent on 2014-10-20
Thanks.

Yes, sorry I had my wires crossed. This is the fault of Nvidia, not Linux.

I checked in System Settings, Details, Graphics, and it said "None found".

To be clear after the upgrade the computer never booted. It would just go into a screen asking me to choose recovery or low graphics mode but not actually go to either of them. The only way I've been able to use it has been to use select a previous version at OS-selection stage of bootup.

Also, sorry, I shouldn't have mentioned Flash. Only reason I mention that is because it needs to be updated, but I can't update my computer at all because I have no graphics driver so I can't use the current version of the system. So my little plan to work around the graphics card problem is going to be short lived because eventually everything will stop working if it's not updated...

Thanks, I will look into [COLOR=#000000]Nouveau driver.[/COLOR]

---

