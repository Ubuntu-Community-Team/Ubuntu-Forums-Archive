---
title: "Grub 17 error"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by Requiemforroksy on 2009-06-22
Hello

I recently thought I would give Ubuntu a try.  I have WIN XP now.I downloaded 9.04 and put it on a CD. Installed it once. It worked fine. I decided to give it more space in the partition (the first time I just gave it 2.5 GB). So I put the CD back it, changed the Windows partition to 700GB and Ubuntu 200GB. (I have a 1TB hard drive). It seemed to install just fine but now when I restart the computer I get a Grub 17 1.5 error. Then it hangs. I tried putting the live CD and also booting Ubuntu from a USB drive, but it does not even get to that screen with the installation options. Basically it does not let me load Windows or Ubuntu, and even though the BIOS is set to boot from CD it does not get to that point because I get the error before. Any ideas, I would be willing to reformat the drive and reinstall Windows but I would like to see if there is anything else I can do. 

Thank you
-REQ

---

### Post by gradinaruvasile on 2009-06-22
"17 : "Invalid device requested"
This error is returned if a device string is recognizable but does not fall under the other device errors."

From here:

[http://www.uruk.org/orig-grub/errors.html]("http://www.uruk.org/orig-grub/errors.html")

If u can, boot from a live cd or usb and follow the instructions from here:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

to reinstall the grub loader.

---

