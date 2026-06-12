---
title: "Audio in new Xubuntu install"
date: 2021-10-21
forum: Hardware
---

### Post by vineyridge on 2021-10-21
Xubuntu 20.04; MSI Nvidia GeForce GT 610; HDMI connection to monitor speakers; no other speakers; computer is vintage 2009, ASUS P5G41-M LE with integrated Intel audio that needs separate speakers.  I  have an old pair of logitech speakers that only work with Windows.

Like so many others, I cannot get this system to use the NVidia sound.  There seems to be no available GUI sound selector available.  I have the NVidia Server on this computer, but when I look at Additional Drivers, I am not given the option to select the NVidia proprietary driver 3.90.  The only available driver is the "manually installed" driver from the OS install.  

I have opened pavucontrol in the terminal and it brings up a window showing both NVidia audio and integrated audio, but a way to select between them is not obvious.  There is a selection button for "fallback audio", but I don't know if "fallback" is the same as "default".  I have just turned off integrated audio in pavucontrol, but shouldn't I need the NVidia driver package for it to work?

 I have also opened "alsamixer" in the terminal, which offers a way to set "default", and it sees both audio outputs. However I cannot figure out how to Enter, as the window does not accept my keyboard; 

I have read and read about how to get NVidia audio and audio to work, and I know there are dozens of questions on this subject, but none of them seem to address the problem in Xubuntu 20.04.
 I will see if turning off the integrated audio makes any difference and post back if it does.

With decent instructions, I am old, ignorant, but game to try to fix this in the terminal.   I have had this issue in Ubuntu before, but there was a GUI way to resolve it. 

Second issue: how do I make the system offer me the choice of other than the manually installed driver.  I have three other choices, including Xorg, but they are all unavailable.

---

### Post by vineyridge on 2021-10-21
Solved.  Turning off the integrated audio in pavucontrol made the HDMI audio work.

---

