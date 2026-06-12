---
title: "Webcam and touchpad problems"
date: 2009-10-20
forum: Hardware
---

### Post by sozgen on 2009-10-20
Hi, I have a Hypersonic Aviator Cx-7 laptop with 9.04 installed on it.
There is two particular problems which i could not solved and hope you can help me solve them.
1) Touchpad: My touchpad is not working. Synaptics is installed by default and set to use touchpad, touchpad m1-m2 buttons are working but touchpad itself is not. I cant remember at 9.04 install but 8.10 installer can use touchpad without problem so maybe its about 9.04 itself or some configuration or program after install.
2) Webcam: My computer does not see monitor attached webcam at all, i managed to install EasyCam2 even with broken python2.4 packages but EasyCam2 can not recognise my camera. I know from my older brother that camera works on a previous ubuntu edition without much problem. Is there any other way to do it?
Is it only me or does 9.04 really hates me and my computer? Should i roll back to 8.10. And if I should how can i do it without loosing much data(/home is not on a seperate partition [shame on me])
It would be very nice if you could help me.

---

### Post by sozgen on 2009-10-22
Refreshing :<

---

### Post by Dark_Stang on 2009-10-22
1. Okay, as long as you don't reformat you shouldn't lose any data. However seperate partitions really are handy.

2. If you're having issues with 9.04, it's okay roll back to 8.10. There's no harm in that, it's just older software. Pop in the 8.10 live CD and reinstall. Just don't reformat.

3. I had an older acer laptop who's webcam wouldn't work until I installed camstream or cheese. So... it might sound weird but try that.

4. The touchpad problem is a little odd. Did you do an upgrade or fresh install to get to 9.04? If you did an upgrade you might want to just try renaming the /etc/X11/xorg.conf file to something like xorg.conf.old and rebooting to try to reset all your input and video devices.

---

### Post by sozgen on 2009-10-22
Thank you for your help.
3. I have cheese installed and did not do any good i tried another random webcam using usb port and it just worked without a problem. So i am back to 0
4. It's a fresh install. I have Nvidia drivers installed which might change xorg files and will try to rename xorg.conf as you said just in case to see what will happen.
Thanks in advance.

---

### Post by sozgen on 2009-10-22
Okay, xorg.conf trick didnt do any good :< Any other ideas?

---

### Post by sozgen on 2009-10-22
By the way my webcam is not listed in /dev/video* so i dont think cheese or camstream(both is installed by the way) will solve it since even they dont see the device.

---

### Post by sozgen on 2009-10-23
Bump

---

### Post by sozgen on 2009-10-24
Re-up.

---

