---
title: "Onboard soundcard ALC259 no sound"
date: 2010-12-12
forum: Hardware
---

### Post by misha1983 on 2010-12-12
Hi, 

I'm using Ubuntu 10.10 with Alsa driver version 1.0.23.

My laptop is an Asus K42Jr with a Realtek ALC259 onboard soundcard.  I'm unable to hear sound through the onboard speakers.  Plugging in external speakers sometimes resolves the problem.

I've Googled around and this seems to be a bug in the drivers:

[http://www.linux-archive.org/ubuntu-kernel-team/426887-alsa-hda-handle-pin-nid-0x1a-0x1b-0x21-alc259-269-a.html](http://www.linux-archive.org/ubuntu-kernel-team/426887-alsa-hda-handle-pin-nid-0x1a-0x1b-0x21-alc259-269-a.html)
[http://permalink.gmane.org/gmane.linux.alsa.user/34278](http://permalink.gmane.org/gmane.linux.alsa.user/34278)

Also, I've noticed that if I boot from the Ubuntu DVD, sound works fine.  If I boot from HDD, I experience the problem above.

So, my questions are:

[LIST]
[*] Am I running into the bug detailed in the above URLs?  How can I check?
[*] It looks like a fairly easy patch, what do I need to re-compile to fix the bug?  Is it ALSA, the Kernel, or something else?
[*] Is it likely that this will be in a release soon?  Will the problem just go away after an update?
[*] Why does booting from DVD work fine, but booting from HDD leads to problems with sound?  How can I diagnose the two configurations and find out what's different?
[/LIST] 

I notice there are some other people with ALC259 problems on the forum, but nobody seems to be pointing to this bug.

Thanks in advance.

Cheers,
Misha

---

### Post by FokkerCharlie on 2010-12-12
Hi Misha

Sorry to say, I am not able to offer you an immediate solution.  but it sounds like I may be experiencing the same problem.  My laptop speakers suddenly stopped working (possibly today, but as I mainly use USB speakers, it could be a few days ago).

So did you have this problem last week?  Does the sound work if you plug in headphones?  (Mine does.)

Cheers
Charlie

---

### Post by misha1983 on 2010-12-12
Charlie, thanks for the reply.  I only installed Ubuntu on this laptop last night, so I can't say whether or not this problem has occurred in the past.

Yes, the sound works when I plug in headphones.  Occasionally, it works normally without headphones as well (I logged in this morning, and the sound worked fine) but this is intermittent.

Cheers,
Misha

---

### Post by FokkerCharlie on 2010-12-13
Hmmm..... 

My problem is now solved, although I'm not completely sure how.

I installed linux-backports-modules-alsa-maverick-generic from synaptic, which seemed to work.  Then stopped working.  Then I uninstalled it, and now everything is OK again.  I really don't know why, but you could also have a go at that...

Also, make sure you double-check gnome-alsamixer to see that all your volume levels are turned up.  I had a moment of despair this morning, but found that was the problem.

Good luck.

Charlie

---

