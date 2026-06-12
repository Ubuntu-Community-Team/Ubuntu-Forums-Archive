---
title: "Not able install ubuntu 12.04 on Intel DH67BL"
date: 2012-08-02
forum: Hardware
---

### Post by lokeshv on 2012-08-02
I have a pc with the follwing spec:

Motherboard: Intel DH67BL 3rd Generation Intel corei7
Hardisk: WE CAVIAR BLACK I TB

when i boot from usb/cd, after the Ubuntu logo the screen becomes grey and not able install.

Anybody faced the problem? Is there any solution?

---

### Post by oldfred on 2012-08-02
Welcome to the forums.

What video card/chip are you using.

Often nVidia and some others need nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Some very new (like yours) or very old systems also require extra boot options also. But try the nomodeset first.

You should be able to hit any key as soon as the little accessibility icons at the bottom appear (keyboard & person). Then press f6 to choose nomodeset.

Is this also a UEFI system or BIOS?

---

### Post by lokeshv on 2012-08-21
> **oldfred said:**
> Welcome to the forums.

What video card/chip are you using.

Often nVidia and some others need nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Some very new (like yours) or very old systems also require extra boot options also. But try the nomodeset first.

You should be able to hit any key as soon as the little accessibility icons at the bottom appear (keyboard & person). Then press f6 to choose nomodeset.

Is this also a UEFI system or BIOS?
Hi,

Thank you very. The Problem Solved. I installed according your instructions, its working perfectly. I am using Nvidia GT240 and set the NOMODESET while installing and before the first boot. I installed latest Nvidia drivers. Its working perfectly. I don't know whether i am using uefi OR BIOS

I thought i wanna wait till the next Ubuntu's release i.e Ubuntu 12.08 and with your instructions i am able to run Ubuntu on this new motherboard.

---

### Post by oldfred on 2012-08-21
Glad you got it working. :)

You can post solved.

---

