---
title: "need help to get 3d working"
date: 2008-09-05
forum: Hardware
---

### Post by Deo Favente on 2008-09-05
ok im getting really tired now. can't get opengl to work same old error: cannot find matching glx visual

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)
i have intel 945, theres no instructions on that, theres nothing in hardware drivers window

I'm just trying to play games like sauerbraten and urban terror. What do i do?

---

### Post by Deo Favente on 2008-09-06
I think it has to do something with not being able to switch resolutions, as the game im trying to play is configured to run in 640 x whatever. how do i make my monitor change screen resolutions?

---

### Post by Deo Favente on 2008-09-09
Double post

---

### Post by ice2921 on 2008-09-09
Just so you know intel does make linux drivers specifically for that card. You can find them here [http://www.intellinuxgraphics.org/documentation.html]("http://www.intellinuxgraphics.org/documentation.html") Also I know that integrated graphics card work i used to have one.

---

### Post by Deo Favente on 2008-09-09
3d games still don't work tho. How do i set it up properly, so that 3d works and i can chage resolutions?

---

### Post by Deo Favente on 2008-09-09
I took at look at X0rg.0.log and this is the errors and warnings that i found:
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd0000009
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(EE) intel(0): [dri] I830CheckDRIAvailable failed: glx not loaded
(WW) intel(0): EXA greedy migration mode enabled.
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
(WW) Configured Mouse: No Device specified, looking for one...

Does this help?

---

