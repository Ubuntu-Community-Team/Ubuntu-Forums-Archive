---
title: "yet another audio problem"
date: 2015-07-20
forum: Hardware
---

### Post by bandito40 on 2015-07-20
I have a Acer Chromebook 720 that I installed CrUbuntu on.  I use it as a media player connected to my tv and stereo.  I was playing around with some commands I found online to control the volume from the command line (telnet).  None of them work but I now have a problem.  If I raise the volume on the notebook or stereo enough so I can hear it properly I get intense feedback/reverb. Also I to type one the keep board (directly on the notebook) or tap it I can here that also which is very loud. It's like my Chromebook has become a amplified microphone. Does anyone know how to reset the audio setting back to spec?

---

### Post by sandyd on 2015-07-20
> **bandito40 said:**
> I have a Acer Chromebook 720 that I installed CrUbuntu on.  I use it as a media player connected to my tv and stereo.  I was playing around with some commands I found online to control the volume from the command line (telnet).  None of them work but I now have a problem.  If I raise the volume on the notebook or stereo enough so I can hear it properly I get intense feedback/reverb. Also I to type one the keep board (directly on the notebook) or tap it I can here that also which is very loud. It's like my Chromebook has become a amplified microphone. Does anyone know how to reset the audio setting back to spec?

Its possible that you've enabled the mic, which is now causing echo.

Try using pavucontrol to mute the mic (Install Pavucontrol via terminal, or search for "Pulse Audio Volume Control" from Software Center)

---

### Post by bandito40 on 2015-07-29
I tried that but no luck.  Tried to reinstall ubuntu but the install is not going correctly.  Thanks however.

---

