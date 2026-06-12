---
title: "Audio device acting REALLY wierd"
date: 2009-10-09
forum: Hardware
---

### Post by lupidan on 2009-10-09
Hello.
I am having some problems with audio in my Ubuntu 9.04.

When I was in Ubuntu 8.10, the audio device didn't work properly, to silence the speakers and hear from earphone output, I had to silence every track manually and only leave the Surround active. It was a bit of an anoyance but I didn't care.

Now, I have installed Ubuntu 9.04, and as always, I tried the same process but now the surround channel does not appear. So I silenced a PCM track, didn't work, then activated it again and I can't hear ANY SOUND, just random bzzz. It worked before so I really don't get it.

It was a clean installation, the only thing I installed was Flash for youtube videos to try sound....

lspci
...
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
...

Thanks and sorry for the inconveniences :)

PD: Ok, reading trough this forum I found that the problem was the PCM channel, it was low, so the random bzz are fixed.
However, the earphones do not work anymore, is there any way to fix it? Thanks in advance

[B]Ok, solved. Just edited the /etc/modprobe.d/alsa-base.conf
adding at the end
options snd-hda-intel model=auto

¿Why it's not set by default? It works perfectly :S[/B]

---

