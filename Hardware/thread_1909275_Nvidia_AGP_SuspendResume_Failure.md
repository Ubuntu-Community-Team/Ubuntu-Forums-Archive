---
title: "Nvidia AGP Suspend/Resume Failure"
date: 2012-01-14
forum: Hardware
---

### Post by Maximus559 on 2012-01-14
Just upgraded to Xubuntu 11.10... figured it was time to have another go at fixing this problem.

I've been using Ubuntu on my Dell Dimension 4500 since 9.10, and it's always had the same problem with suspend. Specifically, the system will suspend to RAM just fine, but when I try to resume, everything turns on except the display. Fans whir, LEDs blink, but the monitor stays black until I do a hard reboot.

From what I've read on the forums, it seems that this problem affects AGP graphics cards from Nvidia which use the nvidia-96 drivers. My Geforce4 MX 420 is such a card. Apparently, some Ubuntu users were able to fix this problem in the past by adding the "NvAGP" "1" option to xorg.conf. From what I understand, however, Ubuntu no longer uses xorg.conf, so I'm not sure how to proceed.

Has anyone been able to successfully resolve this problem on a current version of Ubuntu?

---

### Post by 2F4U on 2012-01-15
Ubuntu can still use xorg.conf. It is not there on a default installation since the X server is able to automatically detect the graphics settings. But if you need special settings you can still create xorg.conf and the X server will then use that settings.

---

### Post by Maximus559 on 2012-01-15
Well, I tried adding the NvAGP option to my xorg.conf file... no effect. Wasn't much in that file, which makes me think it's not really being used.

Any other ideas?

---

