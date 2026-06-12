---
title: "Disable Laptop Speakers in VAIO VGN-TT16GN"
date: 2009-07-02
forum: Hardware
---

### Post by plaknas on 2009-07-02
Hi,

I run a dual-boot with Vista and Ubuntu "Jaunty" which was installed using Wubi. In Vista when I connect speakers or noise-reducing headphones, the laptop speakers automatically get disabled. However, that is not the case with Ubuntu.

I have tried some of the solutions mentioned in these forums such as installing KMix and then modifying the alsa-base.conf file to add a string "options snd-hda-intel model=....." When I try Vaio or laptop with the model it makes no difference. However when I use model=3stach-6ch and reboot I get the option in the KMix mixer to disable Front wihich is the laptop spekaers. The problem I am facing is that this works for only one reboot. If I reboot, the options are there but it makes no difference. I have to delete that line, reboot and then add it and reboot again to get it working.

Does anyone have any solution for this? Is this because of the way I installed Ubuntu?

---

