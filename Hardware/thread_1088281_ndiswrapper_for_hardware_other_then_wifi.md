---
title: "ndiswrapper for hardware other then wifi?"
date: 2009-03-05
forum: Hardware
---

### Post by mulder_edu on 2009-03-05
Can you use ndiswrapper to install Windows drivers for other hardware besides wireless?  I just tried it to install my sound card.  ndiswrapper recognizes my sound card with the Windows driver installed and detects the hardware, but how would I integrate it in Ubuntu?  Ubuntu doesn't seem to recognize the sound card still (other then through ndiswrapper).

---

### Post by lavinog on 2009-03-05
I think ndiswrapper is only for network drivers.

What sound card do you have.
Surely someone knows how to get it working.

---

### Post by mulder_edu on 2009-03-06
In answer to my own question, no, audio drivers do not work with ndiswrapper.  It hosed my xserver somehow on reboot.  Even uninstalling the driver didn't bring it back up. I'm reinstalling Ubuntu now ](*,).
I've got a ali M5451 sound card.  It's supposed to be supported by ALSA, but it hasn't worked the last couple of distributions.  Nobody seems to know what's wrong with it.  I can't get it to work in OSS either.  Here's my thread for that issue:  [http://ubuntuforums.org/showthread.php?t=1029515](http://ubuntuforums.org/showthread.php?t=1029515)

---

### Post by mulder_edu on 2009-03-07
I got my audio to work.  It was a hardware problem.  I left a piece of tap on my sound card when I opened it to fix the cpu fan last month.  The tap got stuck inside the port between the card and the systemboard.  I took it out and the sound works fine.

---

