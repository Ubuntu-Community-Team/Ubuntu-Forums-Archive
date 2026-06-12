---
title: "How well does the ASUS P5B work with Ubuntu 6.10 and newer, including Feisty?"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by thewizard5001 on 2007-04-02
How well does the ASUS P5B work with Ubuntu 6.10 and newer, including Feisty? Does everything, including the Realtek 8111B Ethernet NIC and the JMicron JMB363, work out of the box? If something does not work, can you suggest how to get it working? Also, how stable is the computer? Can I expect to keep the computer on for a very long time? How long have you been able to keep your computer on for?

Thanks!

---

### Post by pasipasi on 2007-04-02
Boot the Live CD and see.

---

### Post by thewizard5001 on 2007-04-02
> **pasipasi said:**
> Boot the Live CD and see.

I don't have that motherboard yet.

I need an answer from someone who has had that motherboard for more than 3 weeks.

---

### Post by thewizard5001 on 2007-04-02
Nevermind: [http://www.linuxquestions.org/questions/showthread.php?t=531598&highlight=ASUS+P5B](http://www.linuxquestions.org/questions/showthread.php?t=531598&highlight=ASUS+P5B)

---

### Post by rbm0307 on 2007-04-02
> **thewizard5001 said:**
> Nevermind: [http://www.linuxquestions.org/questions/showthread.php?t=531598&highlight=ASUS+P5B](http://www.linuxquestions.org/questions/showthread.php?t=531598&highlight=ASUS+P5B)

Not 100% accurate.  So long as all your IO is sata attached (CDROM/hdisk) then Ubuntu should work.  I ran Edgy LiveCD from a system similar to yours and it worked fine. For lots of info, see [http://www.win.tue.nl/~aeb/linux/misc/ubuntu_on_core2duo.html]("http://www.win.tue.nl/~aeb/linux/misc/ubuntu_on_core2duo.html").  Also refer to this thread: [http://ubuntuforums.org/showthread.php?t=343298]("http://ubuntuforums.org/showthread.php?t=343298").


Alternatively, the Feisty build from 31 March 2007 is fully functional with IDE devices on the P5B (see [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502") )

---

### Post by kwaanens on 2007-05-10
Just an update.
I'm using the mobo. Works great, straight out of the box on Feisty final.
2 minuses:
- lm-sensors doesn't work (2.6.21 kernel is said to work)
- no wpa on wireless (might work with some tweaking, but did not try much)

- Ketil

---

