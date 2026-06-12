---
title: "Hp pavilion DV 4 Sound Problem"
date: 2009-02-12
forum: Hardware
---

### Post by alexl777 on 2009-02-12
Hello and good day to those who can help me solve my little problem and those who have the same problem will look this thread up in google later.

I have been using vista for a long time, very satisfied, lately decided to go for a dual vista/ubuntu for various reasons.

Ubuntu is a great linux distro, it has so much to offer, apart from being Free OS.

Encountered a minor problem using Ubuntu on my Hp pavilion DV 4 laptop, and that problem is: Sound (or sound drivers), i mean there is sound, but it is very slow, (like in slow motion), and when ubuntu loads there is a weird drum like sound (which was supposed to be the log on sound).

*I have googled for days in search for an answer, found out i am by far not the only one having the same problem, hope someone here will be able to help.

Thanks in advance...

---

### Post by linux_tech on 2009-02-12
I think pulseaudio is likely the cause. There are some tihings to try to get pulse audio working better.  The alternative to fixing it is to 
uninstall it and use other apps like esound.

This sometimes helps improve system sounds- 

```
sudo gedit /etc/pulse/default.pa
```

then change line-
#load-module module-esound-protocol-unix

to  this-
load-module module-esound-protocol-unix socket=/tmp/.esd/socket

You can also turn the system sounds off (disable)
system>preferences>sound>sounds>disable

---

### Post by linux_tech on 2009-02-12
HOWTO: PulseAudio Fixes-
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by alexl777 on 2009-02-12
> **linux_tech said:**
> HOWTO: PulseAudio Fixes-
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

This should prove helpful, i will try this and see what happens.

Thanks...

---

### Post by alexl777 on 2009-02-12
OMG nothing helped!

---

### Post by dexterslab on 2009-02-14
Hi, 

I installed Ubuntu back in december in a DV4-1117nr and what i can tell is that you just need to search this 2 keywords DV4+ubuntu,

to solve your sound problem just need to follow 3 simple steps listed in this thread: [http://ubuntuforums.org/showthread.php?t=984538](http://ubuntuforums.org/showthread.php?t=984538)

1. This should solve your dv4 sound problems:

**gksudo gedit /etc/modprobe.d/alsa-base**

2. and add this to the end of the file:
[B]
options snd-hda-intel enable_msi=1[/B]

3. reboot

---

### Post by alexl777 on 2009-02-15
I will have to try this, thank you.

---

### Post by dexterslab on 2009-10-30
I ran the update manager and installed 9.10 Sound information was remove, however sound worked just fine.
\\:D/

---

