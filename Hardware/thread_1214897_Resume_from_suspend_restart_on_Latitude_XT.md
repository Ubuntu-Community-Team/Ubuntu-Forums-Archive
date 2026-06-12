---
title: "Resume from suspend restart on Latitude XT"
date: 2009-07-16
forum: Hardware
---

### Post by 4Play on 2009-07-16
Hello,
I am runnuing Ubuntu 9.04 on a Dell Latitude XT (tablet), and almost everything is working fine, except for one thing:

sometimes, when I suspend the computer, when I open the lid for it to resume, it shuts down, at the exact moment I open the lid. But this only happens sometimes, say 3 out of 10 times I suspend :(

My system is slightly modified, so that the touchscreen works:

I installed the 2.6.30 kernel (from Karmic, ubuntu 9.10)
I also pulled xserver-xorg-video-radeon and xserver-xorg-core from karmic.
I am using the open source 'radeon' driver, since ati has decided to drop support for my card, and the fglrx dirver no longer works.

I have cheked the system logs and havent found anything useful, only the line:

> syslogd 1.5.0#5ubuntu3: restart.

in the messages log, at the exact moment it was supposed to resume from suspend.

I know this situation is pretty specific, but If someone could give me some pointers on how to further debug this issue that would be great!

here is the pertinent portion of my xorg.conf

> Section "Device"
	Identifier  "Configured Video Device"
	Driver		"radeon"
	Option          "AccelMethod" "EXA"
EndSection

going back to a older kernel version is really last on my list, since that would break the touchscreen (finger input, pen works just fine on older kernels)

thanks!:)

---

### Post by 4Play on 2009-07-18
Well, I seem to have solved the problem by disabling resume on lid open, now I have to press the power button for it to resume. I think this approach might be even better than the resume-on-open-lid.
If anyone else is interested, [this]("http://ubuntuforums.org/showthread.php?t=293883") thread has a good guide on how to disable wakeup on lid open

---

### Post by Favux on 2009-07-18
Hi 4Play,

It sounds like you've solved your problem.  I don't know if it had anything to do with the 2.6.30 kernel.

But Ayuthia has made some deb.s of n-trig patches to the current Jaunty kernel that folks say work better than using 2.6.30.  You also use a xorg.conf along with the patched kernel.  The xorg.conf might give you some ideas even if you're not interested in the patches or deb.s.  See Appendix 2 near the bottom here for the xorg.conf and link to Ayuthia's instructions and deb.s:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)

And a thread to skim through where a couple folks set things up:  [http://ubuntuforums.org/showthread.php?t=1206355&page=2](http://ubuntuforums.org/showthread.php?t=1206355&page=2)

I hope this is useful.

---

