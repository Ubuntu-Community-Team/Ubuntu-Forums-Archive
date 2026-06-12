---
title: "Sound Problems"
date: 2009-10-23
forum: Hardware
---

### Post by kf4mat on 2009-10-23
Hello All,

Okay first yes, another post about sound..... however I have spent the last day and a half researching the forums trying to find the solution on my own. Second I don't want to be spoon fed the answer, when I figure out what the problem is I want to at least try to understand what I am doing to fix it.

My system:

Toshiba Satellite L25 S1192
OS Jaunty 9.04

The problem:

Sound plays on startup and login but when trying to play back music, sound system hangs and all I get is an annoying didadidadida coming from the speakers.

What I have been trying:

First thing I did was follow this thread by markbuntu -

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

I believe I have downloaded everything and followed the directions carefully and now have PulseAudio and several other packages on the system but no joy, so continued with this thread by LordRaiden -

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

My sound card is listed here -

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff31
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
	Memory at d0003400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ATI IXP AC97 controller
	Kernel modules: snd-atiixp

I believe the above means that Ubuntu is detecting my sound card. so then I went here -

[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

and was able to find my sound card chip set listed which is the IXP SB400. With this information in the terminal I typed:

sudo modprobe snd-IXPSB400

but all I am getting in return is -

thomas@thomas-laptop:~$ sudo modprobe snd-IXPSB400
FATAL: Module snd_IXPSB400 not found.

And that is where I am stuck...... If any one can nudge me in the right direction I would appreciate it. Please understand that I am new to Linux and don't understand a lot about configuring systems, but am trying to learn.

Thanks in advance,

Tom

---

