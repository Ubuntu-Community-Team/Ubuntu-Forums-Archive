---
title: "Skype in Ubuntu 9.10 Karmic Koala"
date: 2010-11-07
forum: Hardware
---

### Post by Newbie_777 on 2010-11-07
I am having some issues with the microphone. When I use Skype (skype-debian_2.1.0.81-1_i386.deb) on my Ubuntu 9.10 Karmic Koala, the microphone isn't working at all. My camera works great, but there seems to be some difficulties with enabling the microphone to work. I also have to mention that my microphone is integrated with my camera. I am using skype on my laptop Dell Inspiron 5010, Kernel Linux 2.6.31-22-generic, Gnome 2.28.1 and as previously mentioned Ubuntu 9.10 Karmic Koala... I think I have tried almost everything out... I installed pavucontrol, checked out everything in my sound preferences, removing and installing skype over and over again,with no success. Can anyone help me out? Or has anyone encountered the same problems? Are there any solutions to this? :confused:

---

### Post by ajgreeny on 2010-11-07
I think I remember having to install padevchooser in 9.10 to get some bits of pulseaudio to work properly.  I don't remember exactly what I needed to do with it now, or what I changed in its configuration, but I got everything working as it should.

---

### Post by Newbie_777 on 2010-11-07
I have PulseAudio Device Chooser already installed,it came with pavucontrol. But I really need to get my mic working, so is there any chance you can remember the alterations which you did to get everything working?

---

### Post by ajgreeny on 2010-11-07
Sorry, no I can't.

Run alsamixer in terminal if you have not already done so.  You may find that a needed channel is muted or set too low.

---

### Post by Newbie_777 on 2010-11-08
I tried alsamixer in terminal,again with no success. The microphone still doesn't work.

---

