---
title: "Ubuntu and Sound (a possible fix, and a question)"
date: 2005-09-22
forum: Hardware &amp; Laptops
---

### Post by Soul_Rvr911 on 2005-09-22
Hello everyone,

These forums have been my saviour for a lot of my linux questions (a relative newbie here). I managed to fix the problem I've been having with my sound card (I have an Audigy 2). Running alsamixer and unmuting the "Audigy Analog/Digital Output Jack" fixed my lack of sound (might work for some of you with the same problem).

Now, though, I'm faced with a new problem, one I can't seem to find help for. My webcam (a Logitech Quickcam Communicate, with a built in microphone) seems to be stealing priority for sound output, and because it's a webcam, it breaks my sound  :mad: . What doesn't make sense about that is, it doesn't even support sound output, just sound in. When I run the "Multimedia systems selector" and the camera's plugged in, OSS, ALSA, and ESD all give me a "cannot construct test pipeline" error. Also, no sound will play from any audio program, and they give errors about broken sound output pipelines. But when I restart linux and unplug the camera, everything works fine. How can I fix this? I want to be able to use my webcam in linux, but if that's not possible, I at least don't want to have to unplug it from my computer every time I reboot into linux - that's a hassle. Does anyone know how to go about changing my SB Audigy to being the default soundcard, or at least disabling the camera in linux without having to unplug it?

Thanks in advance,

Lenny

---

### Post by Soul_Rvr911 on 2005-09-22
Well, once again the forums come to my rescue. After another search of the forums, I found this link:

[http://ubuntuforums.org/showthread.php?t=27186&highlight=camera](http://ubuntuforums.org/showthread.php?t=27186&highlight=camera)

which solved my problem! Thanks again everyone, keep up the good work here!

---

