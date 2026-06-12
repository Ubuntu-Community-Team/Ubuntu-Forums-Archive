---
title: "Nvidia error"
date: 2018-03-09
forum: Hardware
---

### Post by thomas_j_marshall2 on 2018-03-09
I dual-boot windows 10 and Ubuntu 17.10 and recently had a problem with the on-board amd r7 graphics not working on my asus board and giving me a basic low resolution.  Despite several attempts to fix it (problem with windows not Ubuntu!) I bought a Nvidia Geoforce GT 1030.  Has solved the graphics issue in Windows but caused it in Ubuntu.  Ubuntu was using x-11 (or x-org?) and giving me a basic low resolution so I installed the proprietary driver in software manager and ran in to the boot loop starting/stopping user manager error.  I have followed several fixes on the forums, I used recovery to remove all nvidia drivers but if I re-install the problem re-occurs.  What do I need to do to fix it?

---

### Post by T.J. on 2018-03-13
I'm not trying to tell you your business, but if you want stability you should be using 16.04 LTS for the present.  17.10 is intended for advanced users or developers who do not mind risking breakage.

That said, it sounds like your driver was not installed configured properly.  This can happen on rare occasions, and can be fixed.  Generally, you need to install the driver, and then you should make absolutely certain that the /etc/X11/xorg.conf file exists and is configured properly before you reboot.  If you do not have one, you can usually create a working file using nvidia-xconfig as root - e.g sudo nvidia-xconfig.

Then reboot and it should work.  If it does not, or you need more detailed advice, please post back and I'll walk you through the process of repairing your install and installing the driver.

---

### Post by mörgæs on 2018-03-14
Suggesting to downgrade software while upgrading hardware is not sound advice. @thomas_j_marshall2, you should stay with 17.10.1 which is both a highly stable release (when running in Xorg mode, not Wayland) and has the best hardware support.

---

### Post by T.J. on 2018-03-14
While I do not wish to seem argumentative, Ubuntu is usually based on Debian Unstable, and a lot of bugs are imported wholesale from the Debian Unstable repository.  I've used Debian for about 15-20 years, and Ubuntu off and on since it began, and that has not changed. LTS versions are far more stable, which makes it the recommended version for normal users - even if the software might be a little stale by bleeding edge standards. I apologize if I seem to be a software Luddite, but as a developer, using non-LTS versions feels like a bad support strategy.

16.04 LTS should have out of the box support for the Nvidia 1030 with the latest revision - they basically all use the same driver.  If it doesn't, then Canonical has gotten really sloppy since I last spent a lot of time on the boards.  So with respect, it is hardly bad advice - unless things have changed. I have a 1060 and as I recall last time I used it, it works well enough.

What Thomas does, of course, is up to him.


Cheers!

---

### Post by monkeybrain20122 on 2018-03-14
Nvidia GTX 1070 works on my 16.04.4 machine with Nvidia 390 so it would work for 1030. There are some good interim releases but IMO 17.10 is not one of them (I have tested it out on a spared machine), no show stopping bug, but many little quirks. In general interim releases' support cycle are too short so unless there are some overriding reasons such as hardware compatibility or buggy LTS (that happens) I would stay with LTS at least on my actual work machines. I have better things to do than to reinstall OS every nine months and do all the testings and tuning etc from scratch (all my systems are highly customized and tweaked for best performance) 

But then OP has installed 17.10 already, if the problem is fixable and there are no other issues I wouldn't recommend doing all the work to reinstall 16.04, besides, dualboot with Win10 is kind of tricky, once you get it to work you don't want to mess with it again (another reason against interim  releases if OP hasn't installed 17.10 already)

---

### Post by T.J. on 2018-03-14
> **monkeybrain20122 said:**
> 
But then OP has installed 1070 already, if the problem is fixable and there are no other issues I wouldn't recommend doing all the work to reinstall 16.04, besides, dualboot with Win10 is kind of tricky, once you get it to work you don't want to mess with it again (another reason against interim  releases if OP hasn't installed 17.10 already)

Fair point, but when 17.10 support drops in about 6 months, he will have to anyway.  My reasoning was to get him on a longer support trajectory with less hassle. Less pain over the long run.  The reason I am making these additional comments is so Thomas can read them and decide for himself from different points of view regarding versions.  The debate doesn't do much to solve his issue though, and so from here on I desist in it.

---

### Post by T.J. on 2018-03-14
Either way, whether 17.10 or 16.04, the process of fixing driver problems should be approximately the same.  The offer is still open, Thomas, if you are interested.

---

