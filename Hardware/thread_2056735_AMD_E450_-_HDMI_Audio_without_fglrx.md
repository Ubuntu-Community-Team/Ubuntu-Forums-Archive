---
title: "AMD E450 - HDMI Audio without fglrx?"
date: 2012-09-12
forum: Hardware
---

### Post by Zephalon on 2012-09-12
Hello,

i have a HTPC with an AMD E450 platform, 2 gb ram and a thumb drive instead of a HDD. I had some problems with Ubuntu 12.04 and installed the latest Lubuntu beta version (12.10). The machine is running far better now. My only problem: i can´t get the HDMI audio to work. The headphone jack works btw. 

ALSA recognizes the HDMI audio hardware but as far as i know i need to install the fglrx (Catalyst) driver to get it to work. I can´t do that (no 12.10 support yet) and don´t want to do that (performance is already great and the driver is not as stable).

Is there any possibility to get it to work without waiting for the next Catalyst version?

---

### Post by marinara on 2012-09-13
interesting, i didn't know fglrx wasn't in 12.10 yet.  I kind of need it to be in there

---

### Post by Zephalon on 2012-09-13
The problem is a broken dependency (afaik). I guess you´ll have to wait for the next Catalyst release in October.

---

### Post by Zephalon on 2012-09-16
Catalyst 12.9 (aka 9.00) with support for 12.10 is now available. But i can´t get it to work *sigh*

---

### Post by marinara on 2012-09-16
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer or]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer")
[https://bugs.launchpad.net/ubuntu/quantal/+source/fglrx-installer-updates](https://bugs.launchpad.net/ubuntu/quantal/+source/fglrx-installer-updates)
[]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer")

---

### Post by Zephalon on 2012-09-16
I still would prefer to get HDMI audio to work without the fglrx driver ;)

---

### Post by marinara on 2012-09-16
can i humbly ask you to file a bug?

---

### Post by Zephalon on 2012-09-17
Is it a bug?

> ATI doesn't support yet the [X.org]("http://X.org") and the kernel of 12.10. Hopefully once 12.10 is in RC, it will support it

[Found here]("http://ubuntuxtreme.com/howto/amd-catalyst-12-9-install-guide-ubuntu/?utm_source=rss&utm_medium=rss&utm_campaign=amd-catalyst-12-9-install-guide-ubuntu"). Anyway, i can confirm that the fglrx 9.00 doesn´t work with Ubuntu or Lubuntu 12.10 (driver can´t be loaded). I´m switching back to 12.04. Unfortunatly that release is not very stable on my system :(

---

