---
title: "Problem with Nvidia"
date: 2010-01-03
forum: Hardware
---

### Post by Serated on 2010-01-03
I have a Nvidia Ge force GT 130m graphics card on a Lenovo idea pad.

I was wondering how to fix the 6 screen problem when i install the driver. Please respond as soon as possible. Thank you for taking your time to read this.

---

### Post by lidex on 2010-01-03
> I was wondering how to fix the **6 screen problem** when i install the driver.

Never heard of that - what exactly is it?

---

### Post by Serated on 2010-01-04
It's supposed to be an error with some nvidia graphics cards, after you install the proprietary driver for nvidia 130m, when it boots, it appears as six screens on your monitor. so if your staring at the screen right now, pretend there are 6 of them , really bunched up so it can fit on the monitor, like 6 pieces equal.

---

### Post by lidex on 2010-01-04
Ah. Have a look here:
[http://ubuntuforums.org/showthread.php?t=1234165]("http://ubuntuforums.org/showthread.php?t=1234165")

---

### Post by Serated on 2010-01-04
Oh i looked into that but I am not used to linux or ubuntu. I am new :) ..still learning, so I need help in "decoding" it. Can you give me step by step directions please? Thank you for reading this. Respond ASAP.

---

### Post by cajual on 2010-01-04
> **Serated said:**
> Oh i looked into that but I am not used to linux or ubuntu. I am new :) ..still learning, so I need help in "decoding" it. Can you give me step by step directions please? Thank you for reading this. Respond ASAP.

nVidia already released drivers that fix this issue.  Uninstall your current proprietary drivers from Ubuntu, go to the nVidia website, and download the beta drivers (190.xx or newer).  To install is quite simple:

1. Uninstall your current ones, then download the new ones you want and save to your desktop.
2. Reboot.
3. When you get an error about your xorg.conf, accept **low graphics mode this session** option.
4. Press CTRL+ALT+F1.
5. Type `sudo su` and enter your password.
6. Type `/etc/init.d/gdm stop`.
7. Type `sh /Desktop/Nvidia... (press TAB to complete the name automatically)` and hit ENTER.
8. When it finishes installing, allow nvidia-xorg to make a new configuration file.
9. Type `reboot`.

---

### Post by Serated on 2010-01-05
Do you have a link or screen shot on what the link is. I seem to not be able to find it.

---

### Post by Serated on 2010-01-05
AFter sudo part it's not letting me open file

---

