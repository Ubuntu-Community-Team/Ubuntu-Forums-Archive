---
title: "Driver Ati Radeon HD 4870x2"
date: 2016-03-25
forum: Hardware
---

### Post by lar2 on 2016-03-25
hello guys,
i decided to come back in magic world of ubuntu after many years and i decided using my PC-Desktop. I was a gamers 5-6 years ago and i o.c this PC-Desktop but after 3 years of honored career i diidn't have any nore time to play. Anyway the problem is the drivers of ATI Radeon HD 4870x2, in particular way the software to control my fun speed. I have 3 fan on my video card because i substituted the original fun with Arctic cooling. I tried reading post everywhere, installing packets or follow guides but nothing. So, please, could you help me?
My Ubuntu distribution is 14.4 LTS

Thanks**[B][B][B]**[/B][/B][/B]

---

### Post by mastablasta on 2016-03-25
14.04 means you will have opensource drivers.  you can try with dpm switch. check under KMS power options: [http://xorg.freedesktop.org/wiki/RadeonFeature/](http://xorg.freedesktop.org/wiki/RadeonFeature/)
12.04 is another option until 2017 as it has proprietary drivers available for this card.

---

### Post by lar2 on 2016-03-25
> **mastablasta said:**
> 14.04 means you will have opensource drivers.  you can try with dpm switch. check under KMS power options: [http://xorg.freedesktop.org/wiki/RadeonFeature/](http://xorg.freedesktop.org/wiki/RadeonFeature/)
12.04 is another option until 2017 as it has proprietary drivers available for this card.

Hi, thanks for your h[FONT=arial][/FONT]elp. Finally i found out a way to control the fun and to manage energy consumption. This way the funs are not noisy. I did a substitution in /etc/default/grub [FONT=arial]in this way: 

[/FONT][FONT=arial]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.dpm=1"[/FONT]

[FONT=arial]in

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"




[/FONT]
[FONT=arial]

[/FONT]

---

