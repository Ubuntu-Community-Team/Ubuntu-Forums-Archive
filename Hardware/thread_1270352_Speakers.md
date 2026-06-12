---
title: "Speakers"
date: 2009-09-19
forum: Hardware
---

### Post by linel90 on 2009-09-19
Hello guys..

Just installed ubuntu... but the problem is that my speakers wont work Z cinema Usb speakers?

Any ideaS?

---

### Post by kostkon on 2009-09-19
Give
```
aplay -l
```
in an terminal.

If you can see them listed in the output then your next step should be to install the *PulseAudio Device Chooser* utlity using *Synaptic*.

More info [here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

