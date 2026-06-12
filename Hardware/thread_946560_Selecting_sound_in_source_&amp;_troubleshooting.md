---
title: "Selecting sound in source &amp; troubleshooting"
date: 2008-10-13
forum: Hardware
---

### Post by ziphyre on 2008-10-13
Hello,

I've Hardy installed and Satellite A200 Toshiba laptop. I have 2 input sources, one integrated to the monitor, and one mic jack on the front panel. I have problems with recording sound, in order to troubleshoot I try to enable or disable these source, but I couldn't find how to this. All I can do is mute them.

```
$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

I have no experience on sound configuration with linux, so I don't understand why there is 5 devices listed on Devices option

[IMG]http://s4.tinypic.com/2nrpzfa.jpg[/IMG]

Secondly, I see that my front panel mic is tied to Capture 1. But even I mute the sound like in these picture, the sound is echoed back through speakers?

[IMG]http://i38.tinypic.com/2r46ex4.jpg[/IMG]

And last, I can't record with sound recorder with Capture 1 selected as input. I can hear my sound through speakers but not when I press Play.


Thanks

---

### Post by markbuntu on 2008-10-13
You should be able to mute the microphone in the volume control and leave the capture volumes as they are to eliminate the feedback problem.

---

