---
title: "Lenovo T400 Will Not Wake Up"
date: 2013-02-16
forum: Hardware
---

### Post by buchacho on 2013-02-16
Hello!  I installed 12.10 on this laptop for my mom, and it seemed that the suspend function worked properly.  But it is not now.  I also just did a "partial upgrade" and it is still not working properly.  

Basically, it suspends after closing the lid, showing the lit moon indicator on the case.  After opening the lid, nothing happens, and I have to do a hard reset (pressing the power button 5 seconds).  Then after booting up I get an error to report: "ubuntu 12.10 experienced an internal error".

Thanks for any help that can be provided!

---

### Post by foresthill on 2013-02-16
It's your Intel 4500 MHD graphics. It's a bug going way back to the introduction of version 11.04 in April 2011, and has still not been fixed. 

[http://ubuntuforums.org/showthread.php?t=1741556&page=8](http://ubuntuforums.org/showthread.php?t=1741556&page=8)

Once the backlight goes off, there's no way (that I know of) to get it come back on. A bunch of people fought this bug for months and no one could fix it.

The only solution I know of is to install 10.04 LTS or 10.10 (bad idea since it's no longer supported). AFAIK, 10.04 LTS still has another year of support left, so you might consider that. This is what I'm doing, at least until this is fixed (highly unlikely at this point).

---

### Post by buchacho on 2013-02-17
foresthill, thanks for your reply.  I do find it odd that the suspend function was working initially and now it is not.

---

### Post by buchacho on 2013-02-17
Here is a little more info (might make a difference?):

Graphics: Mobile Intel® GM45 Express Chipset x86/MMX/SSE2 

Here is the error I am getting:

[ATTACH]231562[/ATTACH]

---

### Post by foresthill on 2013-02-17
If the version you upgraded from was 10.10 or earlier, it makes perfect sense to me, since the backlight and suspend problems with the Intel 4500 graphics first appeared in 11.04 (and have still not been fixed) 

But if you originally had version 11.04 or later installed, and it was working, I would suggest reinstalling that version and skipping the upgrade. Or maybe try a live CD of 12.10 or 12.04 LTS.

Upgrades are, IMHO, asking (no begging) for strange problems to happen and I don't know why the option is even offered by Ubuntu. Just look at the threads here and probably half of the people having strange problems with their computers just did an upgrade.

---

