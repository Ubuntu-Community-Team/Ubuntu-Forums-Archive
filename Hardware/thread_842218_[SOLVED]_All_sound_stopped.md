---
title: "[SOLVED] All sound stopped"
date: 2008-06-27
forum: Hardware
---

### Post by brad103 on 2008-06-27
Toshiba Tecra P5 - Hardy

Sound just stopped working. I can't be specific on what happened - nothing that I'm conscious of. I'm now running 2.6.24-19, but I've tried booting into -18, -17 and -16 and still no sound so can't (?) be an upgrade problem. When it first happened (about a week ago) I was using alsa-1.0.16. I tried an upgrade of that just to refresh things and am now on 1.0.17rc2 but still no joy.
I can dual-boot into Windows and sound there is fine, so not hardware.
When I've had the sound modules wrong in the past I'd get the system beep when reaching the login screen and I don't get that now.
dmesg | grep snd shows up nothing (my driver is snd_hda_intel)
I had noticed vlc was not playing sound during the first 5 or so seconds when playing video for the week or so before all sound stopped.
I'm testing the sound by running vlc or using aplay.

Any help appreciated!
Brad

---

### Post by Odrodzona-Sarmacja on 2008-06-27
Try Xubuntu. It is less prone to software conflicts due much less crap programs get installed on it by default. Or try installing ubuntu-minimal package and removing the ubuntu one. So you get less crap software to deal with.

---

### Post by maulik001 on 2008-06-27
this is what I just did to make my sound work on my Toshiba P100

[http://ubuntuforums.org/showthread.php?t=842459]("http://ubuntuforums.org/showthread.php?t=842459")

---

### Post by brad103 on 2008-06-27
Thanks Odrodzona-Sarmacja, but I do have xubuntu!

---

### Post by brad103 on 2008-06-27
Thanks maulik001. My sound has been working fine in xubuntu for about 6 months until now. For me it doesn't sound like a bios problem as that hasn't changed.

---

### Post by brad103 on 2008-07-01
bump. any more ideas, please? I've still been actively searching myself. I installed pulseaudio today after seeing 
> [00000353] pulse audio output error: Failed to connect to server: Connection refused
[00000353] pulse audio output error: Pulse initialization failed
when running vlc from the command line. That didn't help any.

I wouldn't have thought (with what little I know on pulseaudio) that it would be the problem anyway because as I mentioned earlier, aplay produces nothing also.

---

### Post by brad103 on 2008-07-05
Unbelievable! I dual boot with Windows - boot into Windows and **unmute sound**. This fixed it. <sigh>

---

