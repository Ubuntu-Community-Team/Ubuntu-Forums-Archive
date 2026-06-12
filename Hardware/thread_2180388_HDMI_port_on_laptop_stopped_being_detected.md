---
title: "HDMI port on laptop stopped being detected"
date: 2013-10-12
forum: Hardware
---

### Post by cswan on 2013-10-12
I have an Asus S550C. Its HDMI port worked great for video until recently, when I tried to get sound to work. As I have the same Intel video card as this guy, [http://askubuntu.com/questions/278503/no-sound-with-hda-intel-pch](http://askubuntu.com/questions/278503/no-sound-with-hda-intel-pch), I followed his instructions and to my surprise suddenly the HDMI port stopped working even for video.

xrandr no longer lists HDMI, even as "disconnected".
dmesg no longer says ANYTHING when I plug in or unplug the cable to this TV.
aplay -l still lists this 
"card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]  Subdevices: 1/1
  Subdevice #0: subdevice #0"

Returning the /etc/modprobe.d/alsa-base.conf file to its original condition and rebooting has no effect.

Reading these forums has solved hundreds of problems for me in the past, but I couldn't find anyone with this problem here. That's a first for me, so I posted. I hope I followed the correct style to post.

---

### Post by cswan on 2013-10-12
The guy here [https://bbs.archlinux.org/viewtopic.php?id=142661](https://bbs.archlinux.org/viewtopic.php?id=142661) appears to have the same problem, or at least similar symptoms (xrandr does not list HDMI port). Since these answerers thought it was a drivers problem, should I then be trying to fix my i915 drivers?

What are some more diagnostic tools regarding video output to help me pinpoint the problem?

---

### Post by cswan on 2013-10-12
I re-installed the xserver-xorg-video-intel package and the HDMI port is once again listed in xrandr. "HDMI1 disconnected (normal left inverted right x axis y axis)"

---

### Post by cswan on 2013-10-12
This fixed the problem. Is there some procedure now... labeling it "Solved"?

---

