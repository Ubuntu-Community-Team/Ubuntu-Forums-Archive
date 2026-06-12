---
title: "How can I make UEFI on ASUS ROG G501VW ready for Ubuntu installation?"
date: 2016-07-16
forum: Hardware
---

### Post by rezaasl2000 on 2016-07-16
Hi,  

I have a G501VW that I want *preferably* dual boot on, but, I can also completely get rid of Windows 10 and have it a pure Linux machine.  Has anyone had any experience with it?  I have already disabled fast boot, secure boot control,  and disabled CSM (I don't know how I did this last one, but I somehow did)!  I've used the tutorials online for other ASUS laptops to achieve these results, but there seem to be something missing!!

But I can't install Ubuntu or any other distos!  For example, on Ubuntu I get to Grub screen, but choosing Ubuntu will not get me anywhere, or Manjaro and Astergos fail to boot after the initial post-install restart.  

Can anyone help?


Thanks.

---

### Post by oldfred on 2016-07-16
I recommend dual booting or at least a full image backup of Windows, so if need be, you can restore it. Many users find one application or game that is not in Ubuntu, and want Windows back later.

If Ubuntu is installed, use live installer and this:
 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Issues are often common by brand across many models as UEFI is same only options vary.
Often boot parameters are needed for Asus:

 Some have had to turn on CSM/Legacy boot to be able to boot USB flash drive in UEFI mode?
[http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/](http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/)
Asus UX303UB hardware problems - a list  15.10
[http://ubuntuforums.org/showthread.php?t=2319066](http://ubuntuforums.org/showthread.php?t=2319066)
Asus M32CD desktop - Skylake several boot parameters  pci=nomsi  i915.preliminary_hw_support=1
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)
ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)
ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)

---

