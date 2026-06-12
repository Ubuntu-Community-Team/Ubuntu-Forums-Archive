---
title: "Hardy kinit no resume image and low graphics mode"
date: 2009-08-04
forum: Hardware
---

### Post by steveneddy on 2009-08-04
Tried rolling my own kernel not available in Hardy for personal purposes.

Used Kernel Check to do this.

Tried 2.6.28 with Nvidia support.

After installation of kernel at restart the Nvidia software kicked in and tried to install a version of Nvidia driver from website.

I canceled the install and tried to boot into the old Hardy kernel (2.6.24) and had low graphics mode. First it came back with the **kinit: no image to boot** message (or something to that nature). 

xorg.conf had been rewritten so I reinstalled old xorg.conf - no joy.

Tried reinstalling 2.6.24 kernel and Nvidia drivers - no joy.

If I try and download Nvidia drivers and correct kernel modules from repos and enable Nvidia driver in xorg.conf I get low graphics mode.

If I go to tty1 and remove reference to Nvidia driver and reboot then I can at least get a high resolution display but no Nvidia graphics driver sweetness.

If I enable Nvidia drivers It will boot to busybox with **kinit: no boot image** message, which has something to do with Suspend because it won't wake from suspend now.

What have I done wrong? Will I have to reinstall? Can I fix this?

I am on the road and would like to get this done so my production machine will stay running.

I am currently running Hardy but have .iso for Intrepid and Jaunty.

I suppose I could reinstall if repair would be shaky at best and future issue could reoccur.

If re-installation required will 8.10 be a good choice until the next LTS comes out?

Any help appreciated.

Thanks in advance.

---

### Post by steveneddy on 2009-08-06
Mod please close thread - I installed Intrepid (an upgrade from Hardy) to solve my issues and give me the features I desired at the moment.

---

