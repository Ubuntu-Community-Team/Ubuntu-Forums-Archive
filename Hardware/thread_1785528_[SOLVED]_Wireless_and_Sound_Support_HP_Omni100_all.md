---
title: "[SOLVED] Wireless and Sound Support HP Omni100 all-in-one PC"
date: 2011-06-18
forum: Hardware
---

### Post by leandromartinez98 on 2011-06-18
Hello, I'm just posting for the knowledge of others that might be interested: I bought and HP all-in-one Omni100 PC, and I had to follow these steps to get fully functioning hardware:

1 - The internal microphone does not work. Solved with:

  1.1. Install the linux-backports-modules-alsa-generic package.
  1.2. Add these lines to /etc/modprobe.d/alsa-base.conf:

options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes


2 - The wireless card does not work. This is solved by installing
this package:

[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb)

(You can get further information following this thread: [http://ubuntuforums.org/showthread.php?t=1314747](http://ubuntuforums.org/showthread.php?t=1314747))

For the records, the sound card is:

lspci |grep -i audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)

and the wireless card is:

lspci |grep -i wireless
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe

---

