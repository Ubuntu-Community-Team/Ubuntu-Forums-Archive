---
title: "How to install drivers in Vmware?"
date: 2006-12-04
forum: Hardware &amp; Laptops
---

### Post by leesshmily on 2006-12-04
I have installed a Windows XP in Vmware under my Unbuntu OS. Can I install some drivers in that virtual OS? And now it just show that I use some vmware chips. Thanks.

---

### Post by Mike'sHardLinux on 2006-12-04
Which version of VMware are you running? If you are running server or workstation, you can install the VMware tools. This will install the "drivers" that will make the guest OS run smoother.  I don't think you can install the tools in the player version (not sure, though.)

I have been able to install drivers for USB devices like my printer and scanner. I think I even got the ipod to work in the virtual winxp in vmware.

Don't expect to be able to install drivers like chipset or video card, though. VMware is a "virtual" environment, and as such is simulating a computer, so it installs virtual drivers. If for example, you have a nice Nvidia video card, you cannot install the nvidia drivers to get 3D acceleration. You have to use the VMware virtual graphics driver, which doesn't do 3D acceleration IIRC.

---

