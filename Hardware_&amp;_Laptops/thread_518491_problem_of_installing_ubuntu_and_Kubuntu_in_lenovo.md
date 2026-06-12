---
title: "problem of installing ubuntu and Kubuntu in lenovo thinkpad T61P"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by hix on 2007-08-05
Hi there, 

i tried to install Ubuntu and Kubuntu in my thinkpad T61P, but it comes out the following message after I clicked on install Ubuntu from the Ubuntu CD and Kubuntu CD:

" /bin/sh: can't access tty; job control turned off."

Is there anyone experiencing the same problem as I did? Why there is such an installation problem? is it coz the hardware incompatibility of Ubuntu?

---

### Post by wjp.reg on 2007-08-05
What did you use to install?  Did you check the md5sum of the CD?  Did you burn a CD?

---

### Post by hix on 2007-08-06
I made the data verification when I burn the Ubuntu CD with the iso file I downloaded. The problem comes in again. 

At first I was worrying about the WXGA may not be compatible with Ubuntu, so I chose the option "run Ubuntu with the appropriate graphic mode", but still the same problem.

Do you guys have any idea?

---

### Post by wjp.reg on 2007-08-06
> **hix said:**
> I made the data verification when I burn the Ubuntu CD with the iso file I downloaded. The problem comes in again. 

At first I was worrying about the WXGA may not be compatible with Ubuntu, so I chose the option "run Ubuntu with the appropriate graphic mode", but still the same problem.

Do you guys have any idea?

Can see that you should have any problems running ubuntu on your intel-based system.

maybe this link will help: [Installing Ubuntu 7.04 (Feisty Fawn) on a ThinkPad T61]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61#Intel_Graphics_Media_Accelerator_X3100_.28Chipset_GM965.29_.28Solved.29")

---

### Post by czheng on 2007-08-18
I had the same problem with my T61. Had to go into BIOS and set SATA to compatibility mode or something like that.

---

### Post by turbage on 2007-08-19
Same, Switch to Compatibility from AHCI, install away.

---

### Post by creedog on 2007-08-19
google man...google.


[http://forums.gentoo.org/viewtopic.php?t=152855]("http://forums.gentoo.org/viewtopic.php?t=152855")

---

