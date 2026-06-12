---
title: "Soundcard drivers listed, but no output options in sound list."
date: 2016-05-21
forum: Hardware
---

### Post by Salketer on 2016-05-21
Hello, I have just upgraded my brand new Dell Precision 7510 from 14.04 to 16.04. I thought that moving to the newest version would be smarter than staying on the old one since I'm new to Linux, better get used to the new first...

So I remember that on the first power up, there was the initial ubuntu setup, and during that set-up there was a music, I remember I could not lower the sound. During the update process, the reboots made a sound when getting to the logging screen. But since the first boot after the upgrade to 16.04, I have no sound.

I am a bit stumped because I'm getting sound through HDMI, and I see the NVIDIA option in the "Play sound through" list in the sound settings. But the problem is that there is nothing listed there when there is no HDMI plugged in. I have checked aslamixer and the random articles I found on the web but nothing has helped... Although I did loose one or two sliders in the alsamixer but I cannot remember what it was.

If someone could help, I'd much appreciate it. Thank you.

---

### Post by Salketer on 2016-05-25
Anyone has any idea? I have not been able to find any other solution...

---

### Post by Yellow Pasque on 2016-05-26
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Salketer on 2016-05-26
[http://www.alsa-project.org/db/?f=ddd63aabc445db22d3706c4d8dcdfe6767c4b1de](http://www.alsa-project.org/db/?f=ddd63aabc445db22d3706c4d8dcdfe6767c4b1de)

---

### Post by Yellow Pasque on 2016-05-26
Your alsa info looks good. Look at pulseaudio next:
```
pacmd list sinks
```

If you want to reset your user's pulseaudio config, run this and then log out/in:
```
rm -r ~/.config/pulse*
```

---

### Post by Salketer on 2016-05-27
Thank you for your help.

The first command lists the 4 applications listed in my sound settings, everything seems about right, all volumes at 100% nothing muted.

I am thinking of switching back to win10 seeing all the small problems I am experiencing, since it is a work station... But thank you for your time.

---

