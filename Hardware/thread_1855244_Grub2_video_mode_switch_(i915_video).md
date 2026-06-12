---
title: "Grub2 video mode switch (i915 video)"
date: 2011-10-05
forum: Hardware
---

### Post by mejo on 2011-10-05
Hello,

My ThinkPad T420 is running Ubuntu Natty and I'm pretty happy with it. One issue that bugs me every time I boot the system is that the video mode seems to be switched between grub2 and initramfs. I first see a blank purple screen (I guess that's hided grub2), then some ugly video mode switch happens, the screen turns black for a very short time, and afterwards I see the initramfs boot splash asking me for the password to unlock my rootfs.

I now wonder whether this behaviour is intended. I thought that grub2 already initialized the correct video mode, and that this avoided later video mode switches. Is this correct?

I'm using the integrated Sandy Bridge video controller (Intel i915).

Greetings,
 jonas

---

### Post by drs305 on 2011-10-05
Does the 'linux' line in your default Grub 2 menuentry include "vt.handoff=7" as an option? That was supposed to smooth the transition.

Colin Watson is Ubuntu's point man on Grub 2 integration. Here is his  response about vt.handoff. Can't say it's a solution to your issue, but it's an interesting paragraph:
[http://www.streamreader.org/askubuntu/questions/32999/what-is-vthandoff7-parameter-in-grubcfg]("http://http://www.streamreader.org/askubuntu/questions/32999/what-is-vthandoff7-parameter-in-grubcfg")

---

### Post by mejo on 2011-10-06
> **drs305 said:**
> Does the 'linux' line in your default Grub 2 menuentry include "vt.handoff=7" as an option? That was supposed to smooth the transition.

Colin Watson is Ubuntu's point man on Grub 2 integration. Here is his  response about vt.handoff. Can't say it's a solution to your issue, but it's an interesting paragraph:
[http://www.streamreader.org/askubuntu/questions/32999/what-is-vthandoff7-parameter-in-grubcfg]("http://http://www.streamreader.org/askubuntu/questions/32999/what-is-vthandoff7-parameter-in-grubcfg")

Thanks for your reply. Up to now, I didn't use this parameter. Now I added it to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub, ran update-grub and rebooted. Unfortunately it doesn't help anything. The video mode switch still happens.

---

