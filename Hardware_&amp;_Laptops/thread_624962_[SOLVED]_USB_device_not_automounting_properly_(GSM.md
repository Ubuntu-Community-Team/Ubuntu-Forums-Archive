---
title: "[SOLVED] USB device not automounting properly (GSM modem)"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by Darksouled on 2007-11-27
Hi!

I have a serious problem about a HUAWEI USB GSM modem not being properly mounted when I insert it, and therefore won't work.

I've come to understand that three nodes should be automatically created (/dev/ttyUSB0, ...USB1 and ...USB2), but when I do, only /dev/ttyUSB0 is. Yesterday I found that all three nodes are created when I boot with the GSM modem already plugged in (and the modem then works as it should), but when I try to remove and plug it in when Gutsy is running, only /dev/ttyUSB0 is created (Shocker: And NOT working).

Made an [**[COLOR="RoyalBlue"]original post[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=622924") about it in the networking forum, but as I believe this forum is a better fit for the problem I hope someone will forgive the double posting. :) Any help is appreciated!

---

### Post by Darksouled on 2007-11-27
[B]Problem solved! 
I managed to find a sweet driver package from the Swedish Vodafone. I installed it and everything seems to work perfect so far. However, as of now the only cards supported are Huawei E620, Huawei E220 and Option GlobeTrotter 3G+ EMEA. It has also only been tested to work flawlessly on Linux 2.6.17 kernels and later. But anyway, Google is my best friend right now. :D[/B]

---

