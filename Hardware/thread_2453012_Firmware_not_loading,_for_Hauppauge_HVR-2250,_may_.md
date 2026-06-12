---
title: "Firmware not loading, for Hauppauge HVR-2250, may be related to 5.3 kernel"
date: 2020-11-01
forum: Hardware
---

### Post by dwsideri on 2020-11-01
Background:
Ubuntu 18.04 LTS, now running 5.3 kernel
TV Capture card: Hauppauge HVR-2250
I have used this card for 8 years back to Ubuntu 12.04, and have succeeded in installing the firmware with 12.04 and 18.04 using instructions at [https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250](https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250).  (Basically, copy the .fw files to /lib/firmware, then add `[FONT=sans-serif]options saa7164 card=8` to /etc/modprobe.d/options). When the card is working properly, two devices exist: /dev/dvb/adapter0 and /dev/dvb/adapter1; all of my DVR software works fine when those devices exist.

Sometime after October 15, 2020, both /dev/dvb/adapterX devices disappeared. When I run `dmesg | grep saa7164`, there is no indication in the log that an attempt to load the firmware was made - no mention at all, the grep is blank.

I've recopied the firmware to /lib/firmware, ran `sudo modprobe saa7164` to no success.

This same issue cropped up in July 2020, when /dev/dvb/adapterX disappeared. I tried reinstalling firwmare, installed the PPA for Hauppauge devices, nothing. Then, a week or so later, /dev/dvb/adapterX reappeared and the capture card worked again. I have *no idea *how it came back.

The only other thing I can point to, and this is going on instinct, is that some kernel update was installed which is causing the firmware to fail to load. I'm now on the 5.3 kernel, but I can't say exactly when it was installed.

Can anyone point me in a direction toward fixing this? I think the starting point is "forcing" the firmware to load, but I'm not finding any guidance on how to do this.[/FONT]

---

### Post by deadflowr on 2020-11-01
Ubuntu 18.04 ships with either the 4.15 kernel or the 5.4 kernel.
I don't think any release of Ubuntu ran 5.3.
To get the 5.4 kernel series you need to install the hwe stack
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

---

### Post by dwsideri on 2020-11-04
Here's the output of `uname -a`:

Linux htpc 5.3.0-64202010201020-generic #0+mediatree+hauppauge~hwe-Ubuntu SMP Wed Oct 21 19:04:50 UTC 20 x86_64 x86_64 x86_64 GNU/Linux

That looks like a 5.3 kernel to me.

My instinct is to back up my data, then do a fresh install of Ubuntu.

---

