---
title: "Latest guidance on Nvidia Optimus Graphics Cards"
date: 2017-05-11
forum: Hardware
---

### Post by jonesyp on 2017-05-11
Hello,

I have a Dell laptop with the Intel / Nvidia combo of graphics cards.  I've been looking around for guidance on installing the correct drivers to get things working, but there seems to be an awful lot of conflicting information out there. Some say use Bumblebee, some say don't.  I did try just installing the recommended Nvidia driver with the 'Hardware' app in Ubuntu, but when I rebooted my system was broken.

I'm using 17.04 64 Bit.

Could anyone point me to some robust documentation if there is any.

Much appreciated.

PS - Is anyone aware of any distros which come with support for Nvidia Optimus out of the box? (Not necessarily Debian based)

---

### Post by efflandt on 2017-05-14
What nvidia chip do you have and which version nvidia driver package did you install (hopefully not a .run file)? Current versions of nvidia drivers have nvidia-prime and graphics device can be switched from "NVIDIA X Server Settings". I just had to log out of X and log back in when switching Nvidia to Intel, but had to reboot when switching Intel to Nvidia. But I did not use **nomodeset** boot parameter (normally required for Nvidia drivers on desktop PC's) because someone said their system did not work when they did that. So maybe that is why my laptop could not load nvidia drivers on the fly when switching Intel to Nvidia.

Your nvidia device may be listed as 3D instead of VGA in output of: lspci

---

### Post by jonesyp on 2017-05-20
Hi,  Sorry for the delay in my reply. I have been on holiday.

I'm using an GT 750M, alongside my Intel Graphics Controller on a Dell Inspiron.

I have now been able to get things working by installing the 340.102 driver from 'Additional Drivers'.  I have previously installed 375.39 from 'Additional Drivers' which had broken things.

I understand that I can now switch graphics cards with Nvidia Settings & Prime. Is Bumblebee still active as a project?  I ask because being able to run specific applications with a chosen card like you can in Windows appeals.

Thanks

---

