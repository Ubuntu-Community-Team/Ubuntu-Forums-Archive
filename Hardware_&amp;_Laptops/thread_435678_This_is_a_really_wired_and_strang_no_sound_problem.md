---
title: "This is a really wired and strang no sound problem! Please somebody help me !!!"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by zhfm622 on 2007-05-07
My ubuntu (v7.04) can recognize my sound card, alsamixer works well, and of course i didn't mute anything. 
 
Here are results from some commands.
> $ lspci 
 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01) 

$ aplay -l 
card 0: SB [HDA ATI SB], device 0: ALC260 Analog [ALC260 Analog] 
Subdevices: 1/1 
Subdevice #0: subdevice #0

I really don't know what i should now....

---

### Post by teaker1s on 2007-05-07
one make sure that the program and soundcard are both using ether alsa or oss output.
secondly sometimes alsa needs model specified in config file.

---

### Post by zhfm622 on 2007-05-07
> **teaker1s said:**
> one make sure that the program and soundcard are both using ether alsa or oss output.


But how?

---

### Post by teaker1s on 2007-05-07
double click volume control and select file and change device-select alsa mixer

then program options or preferences and select alsa

take a look here
[http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383")

---

