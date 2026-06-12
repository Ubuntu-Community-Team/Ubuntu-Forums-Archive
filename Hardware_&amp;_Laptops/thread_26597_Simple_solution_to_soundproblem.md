---
title: "Simple solution to soundproblem"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by Erikhh on 2005-04-13
For days I have tried the suggestions here to make my VIA8235-soundcard work. To no use. Yesterday I suddently stumbled over the solution:

open alsamixer in a terminal

use arrowkey to move to the PCM pillar. Tjek, that it is not mute. Else press m to unmute it

use arrowkey to move to the IEC958 Capture Monitor pillar. Press m to make it mute

press esc-key to save and escape.

Then, there is sound on my computer.

I havn't had time to play with the quality of the sound (which is good), but according to dmesg I have to insert a line in /etc/modprobe.d/alsa-base. There are several possibilities:

snd-via82xx dxs-support=1
snd-via82xx dxs-support=2
snd-via82xx dxs-support=3
snd-via82xx dxs-support=4

---

