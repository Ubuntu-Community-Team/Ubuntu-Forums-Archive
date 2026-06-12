---
title: "VAIO TX3 with Ubuntu 11.04 won't suspend (after suspending once)"
date: 2011-09-15
forum: Hardware
---

### Post by WerKKill on 2011-09-15
Hi! I have a VAIO TX3 with dual-boot Ubuntu/XP. I just upgraded Ubuntu from 10.04 to 11.04.

Problem:

In Ubuntu, the first time I suspend after a reboot, the laptop suspends and wakes up normally. However, if I try to suspend after waking up from the first suspend, the laptop won't suspend again. It just makes the screen go blank (or starts the screen saver). Network connection is also cut.

Before the upgrade suspend was working ok.

Any ideas what could be done?

This didn't work: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

---

### Post by Duncan P on 2011-09-19
I have exactly the same problem on an HP Pavilion dm1 with 11.04. I first noticed it after I used wireless networking for the first time, about 3 months after installing 11.04. Could it be related.

---

### Post by OpenSage on 2011-09-21
> **WerKKill said:**
> Hi! I have a VAIO TX3 with dual-boot Ubuntu/XP. I just upgraded Ubuntu from 10.04 to 11.04.

Problem:

In Ubuntu, the first time I suspend after a reboot, the laptop suspends and wakes up normally. However, if I try to suspend after waking up from the first suspend, the laptop won't suspend again. It just makes the screen go blank (or starts the screen saver). Network connection is also cut.

Before the upgrade suspend was working ok.

Any ideas what could be done?

This didn't work: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)







I know this is a really late reply, but I think I have this issue figured out. I have had the same problem running both Ubuntu 10.10 64 bit and Ultimate Edition 9/on Ubuntu 10.10 64 bit. I came across this fix by accident. Before suspending the machine, go to a different console by pressing (CTRL+ALT+F2) all at the same time. You should be in a new console. Log into that console then press (CTRL+ALT+F7) to take you back to your Graphical User Interface and then Suspend you machine. This works for me every time (although I never hibernate, so don't know if it will fix that). Hope this helps some people.\\:D/

---

### Post by Duncan P on 2011-09-22
So, having an evening when the dm1 was doing nothing I reinstalled 11.04 from the distribution CD. Suspend and resume worked fine multiple times.
Applied all the recommended updates to date. Now it will only suspend once.
So it's something in one of the 240 updates that get applied to a clean machine.
I suppose I could apply them one at a time ...

---

### Post by Duncan P on 2011-10-14
This seems to have gone away with 11.10 to which I upgraded today. Mind you I had to install the gnome desktop (which is no longer bundled) and it dropped all my visual preferences, but still a small price to pay for a working suspend button.

---

