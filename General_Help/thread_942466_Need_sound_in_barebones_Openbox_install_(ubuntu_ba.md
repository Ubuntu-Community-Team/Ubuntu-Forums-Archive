---
title: "Need sound in barebones Openbox install (ubuntu base)"
date: 2008-10-09
forum: General Help
---

### Post by shawnrgr on 2008-10-09
I've installed only ubuntu-base xorg openbox and nvidia-glx. Have the nvidia drivers working along with gtk2 themes. However I can't figure out which packages are needed to get audio working. I installed alsa-base and rebooted thinking maybe thats all I would need but its not working.

Can anyone point me in the right direction as to which packages need to be install for audio to work properly? (audio works without issues on this laptop with ubuntu-desktop)

---

### Post by shawnrgr on 2008-10-09
Found a resolution... Sorry for not searching first. I'm not home but will try this later tonight. [http://ubuntuforums.org/showthread.php?t=849646](http://ubuntuforums.org/showthread.php?t=849646)

---

### Post by urukrama on 2008-10-09
Did you unmote the sound channels? By default they are muted.

Type alsamixer in a terminal and then press 'M' for each channel that you want unmuted (indicated by MM) and move with the arrow keys between the channels. Press Esc to exit alsamixer.

Alsamixer is part of alsa-utils, which is I believe installed by default.

---

