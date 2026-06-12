---
title: "Ubuntu 11.04 Radeon HD 6650m driver problem"
date: 2011-08-07
forum: Hardware
---

### Post by spemsy on 2011-08-07
I got a Acer Aspire 7750g-6444 laptop and installed Ubuntu. It automatically selected fglrx a the video driver and installed. The problem is that it doesn't behave like it's installed. Minecraft crashes after login (an easy game to test graphics) and when I open Catalyst Control Center it says either the driver isn't installed properly or it isn't installed. I have tried removing fglrx and reinstalling. Any ideas?

---

### Post by .... on 2011-08-08
You have hybrid/switchable graphics (Intel IGP, Radeon discrete card). fglrx/Catalyst isn't going to work unless you have a BIOS option to disable the Intel GPU. Other than that, you have to use vgaswitcheroo to switch between the two GPU's and that only works with open-source drivers.

---

### Post by ramden on 2011-09-08
same situation here. 10.10/11.04 seem not to install it right. Is there any other possible workaround to switch off the secret gpu, besides BIOS. Found something similar here : [http://forums.mydigitallife.info/threads/24483-Switchable-Graphics-Ubuntu-10.10](http://forums.mydigitallife.info/threads/24483-Switchable-Graphics-Ubuntu-10.10) . Help me get rid of windows, please !! only graphics holding me back

---

