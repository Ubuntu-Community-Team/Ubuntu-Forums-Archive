---
title: "How are speaker numbers assigned for alsa speaker-test?"
date: 2015-08-09
forum: Hardware
---

### Post by PeterTaps on 2015-08-09
Folks,

ALSA utility speaker-test has a parameter "-s" to test individual speakers. I have a script since Ubuntu 12.04 that I used to test each speaker in my 5.1 system. However, in Ubuntu 14.04, although the script works, the speaker numbers seem to be different. For example, center speaker used to be number 5 but now is number 2.

I am wondering how the speaker numbers are assigned and why they changed in 14.04. Also, if two computers are running the same version of Ubuntu 14.04, is it possible that the speaker numbers may be different?

Thank you in advance for your help.

Regards,
Peter

---

### Post by efflandt on 2015-08-09
Something seems strange. **man speaker-test** for **-s** says "The channel number corresponds to left, right,  rear-left,  rear-right,  center,  LFE,  side-left, side-right, and so on." But with analog stereo speakers, **speaker-test -s 1** says in its output that it is "Front Left", but it seems be equal in both speakers. And **speaker-test -s 2** throws an error "Invalid parameter for -s option." So that does not match up with what the man page says in 14.04.

There are wav files in /usr/share/sounds/alsa/, but when testing those I just realized they are mono files, so aplay does not specifically play them through the speaker of their filename, unless you can figure out how to do that. **Sound Settings** gui speaker test plays through individual speakers, but not sure how it does that.

---

### Post by PeterTaps on 2015-08-10
What is also strange is the numbers that are displayed when you simply play "speaker-test -c6 -twav." Here is what I see on my system:

[COLOR=#000000][FONT=HelveticaNeue] 0 - Front Left[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue] 4 - Center[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue] 1 - Front Right[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue] 3 - Rear Right[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue] 2 - Rear Left[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue] 5 - LFE

Although each speaker plays correctly, I don't understand what these numbers are.

Pradeep[/FONT][/COLOR]

---

