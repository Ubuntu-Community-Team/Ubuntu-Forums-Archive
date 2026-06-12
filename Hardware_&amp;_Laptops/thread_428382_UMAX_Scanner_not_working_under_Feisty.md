---
title: "UMAX Scanner not working under Feisty"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by CK1 on 2007-04-30
I have a UMAX Astranet ia101 scanner that was working under Edgy but no longer works under Feisty. When using xsane, the scanner is detected but it does not turn the lamp on when scanning. The scan bar does move up and down and the scan image produced is totally black. The scanner works ok under windows xp.

---

### Post by coderipper on 2007-04-30
I'm having the same problem since switching from Edgy to Feisty.  My scanner is a Cannon N1240U, which is fully supported by the SANE Project.  I verified that the scanner still works plugging it into my Dapper box and running XSane.

Also, I have tried switching off Beryl in favor of Metacity but it didn't seem to matter.  The software properly identifies the scanner but it doesn't activate the scanner or lamp and returns a blank (black) scan.

The problem is not strictly an XSane problem as the GNOME Scanner Utility and Kooka perform in a similar manner.  Also, attempting to aquire from GIMP only launches XSane with the same result.

For the record, I am running AMD64 Feisty on a GIGABYTE GA-K8NXP-SLI with an Athlon 64 x2  3800+ CPU and 2GB of system RAM.  The scanner functioned perfectly on the same box before doing a clean installation of Feisty.

Any help that can be provided on this is greatly appreciated.  I am a heavy user of this particular piece of equipment.  Thanks in advance.

coderipper

---

### Post by Stinger on 2007-05-01
CK1 , coderipper
It seems to be a kernel bug , but I dont understand how this kinda regression could pass unnoticed into the final release of Feisty ???

You can read more about it here
[URL="http://82.211.81.186/showthread.php?t=389113"]
http://82.211.81.186/showthread.php?t=389113[/URL]

or here
[URL="http://82.211.81.186/showthread.php?t=414474"]
http://82.211.81.186/showthread.php?t=414474[/URL]

bugs are here

[https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488]("https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488")

here
[URL="https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/93515"]
https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/93515[/URL]

and here

[https://bugs.launchpad.net/ubuntu/+source/libusb/+bug/99802]("https://bugs.launchpad.net/ubuntu/+source/libusb/+bug/99802")

Kernelbug here
[URL="http://bugzilla.kernel.org/show_bug.cgi?id=8231"]
http://bugzilla.kernel.org/show_bug.cgi?id=8231[/URL]

Notice ! there seems to be a fix , now we can only wait until the developers decide to patch the current kernel.

As a temporarely workaround "scan button daemon" can be used
Read about it here
[URL="https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488/comments/141"]
https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488/comments/141[/URL]

What a mess...

---

### Post by CK1 on 2007-05-02
Thanks Stinger,  the workaround has worked.

---

### Post by jeanjean84 on 2007-05-04
Hi,

after upgrading to Feisty, my scanner Epson Perfection 660 (using snapscan) stopped working  :( 

I searched around and found the Bug #85488 in linux-source-2.6.20 (Ubuntu) where fishor proposed a  kernel recompiled without USB_suspend :

[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488)

fishor's fix (i.e. recompiled kernel) is working perfectly for me ! 

I have a desktop and no proprietary drivers, ... so no problem !!! 

Xsane works ! gscan2pdf works ! xscanimage works ! scanimage works !

Everything works (so far) !  :lolflag: 

Thanks, fishor !  :)

---

### Post by leg3 on 2007-05-15
I have a different problem with umax 2100U USB scanner. Scanner acquires picture but the colors are awful and there are various colored bands on scan from top to bottom. This scanner worked fine on first attachment on same computer with Ubuntu 6.06 LTS installed . 

Switched to SUSE 10.2 because Ubuntu 6.06 LTS kept crashing firefox browser but suse did not support scanner. Installed Ubuntu 7.04 with clean install and happy to see firefox very stable and not crashing. Liked better printer support than in suse, but then tried to scan with resulting unusable, awful results.

---

### Post by hbiaou on 2007-06-02
> **CK1 said:**
> I have a UMAX Astranet ia101 scanner that was working under Edgy but no longer works under Feisty. When using xsane, the scanner is detected but it does not turn the lamp on when scanning. The scan bar does move up and down and the scan image produced is totally black. The scanner works ok under windows xp.

Hello CK1

I also have a UMAX Astranet iA101 and the same problem. I will try the solution proposed by Stinger.  As it works with you it should with me as well (...I hope...).

Also I could not find the appropriate windows xp drivers for this scanner. I am curious how yours was working under winxp??? Were did you find the drivers ? Please tell me ...

Thanks to you all

---

### Post by CK1 on 2007-06-03
Hi  hbiaou, under XP it worked with the standard loaded XP drivers but I had to start the scanner by selecting the "Printers & Other hardware -> Scanners & Cameras" section of control panel.

---

### Post by dyrk on 2007-08-03
hello leg3
Also have an Umax 2100U. I have never get it to run and tried it with the ubuntu repositories and the sane distribution. How did you get it to run?
Thanks in advance

---

### Post by leg3 on 2007-09-16
Sorry for the delay. Lost interest in thread when I learned the poor scans were the result of Feisty build with rather poor prospects for correction of situation. Maybe next release. I did nothing special. I have an old IBM netvista 1.8gHz P4. The scanner is detected on plug in but the scans are very poor quality with the multibands of color. Print is legible but only good for text. Pictures useless. Very recently retried scanner with same results after all updates to system current.

---

### Post by leg3 on 2007-09-16
Sorry for second post. Used Xsane program. Scanner does seem sensitive to order of plug in usb first then plug in power.

---

