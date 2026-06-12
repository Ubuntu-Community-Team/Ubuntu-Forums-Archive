---
title: "So my sound suddenly doesn't want to work now"
date: 2018-12-01
forum: Hardware
---

### Post by winterwail2391 on 2018-12-01
was working fine earlier today but now ubuntu has decided to be stupid with my chromebook pixel 2013. any ideas what to do?
i have version 18.04 lts

---

### Post by yancek on 2018-12-01
Were any changes made that might affect the sound?  Could you post the output of the commands below which should give some information on your sound?

> aplay -l
sudo  lspci -v | grep -A7 -i "audio"

---

### Post by ra7411 on 2018-12-01
That has happened to me occasionally with Ub 14.04, 16.04 and a few days ago 18.04.  As far as I can remember, always when waking up from suspend.

I always check Pulse volume control, and see that the sound scales are moving showing that audio is working at some level, but not going all the way through to speakers.

The only way out is to reboot, and then audio is fine for 20 or 30 suspend / wakeups.

I think audio is a weak spot in Ubuntu and could stand some re-working.

---

### Post by winterwail2391 on 2018-12-01
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: CA0132 Digital [CA0132 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Google, Inc. 7 Series/C216 Chipset Family High Definition Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at e0500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link

it seems to be working now but is it a hardware issue?

---

### Post by yancek on 2018-12-01
> it seems to be working now but is it a hardware issue? 		

Do you have another OS installed and if so, do you have the same problem with it?  I have a similar problems with my HP laptop on which the sound sporadically fails/works.  I have several operating systems on it and the sound sometimes fails and sometimes works on all of them.  If you have another OS installed or another Linux system you could test on it.  In my particular case, I expect it is hardware but have no solution.  Good luck with it.

---

