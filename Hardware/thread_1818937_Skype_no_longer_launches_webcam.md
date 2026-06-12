---
title: "Skype no longer launches webcam"
date: 2011-08-05
forum: Hardware
---

### Post by tkoopa on 2011-08-05
I've got two machines ( desktop and laptop ), both running natty 64bit which suddenly no longer allow Skype to launch webcams. On both machines the webcam works fine in cheese, google+, ... and Skype launched the webcam fine about a week ago. The webcams are listed in Skype's video settings, it's just that I can't launch the video chat. Anyone have any suggestions on what may be wrong ?

---

### Post by TenPlus1 on 2011-08-05
I had the same problem with skype and fixed it by creating a small script...  Open your text editor, put the following 2 lines and save as 'skypefix' then right-click and select properties and under permissions make it executable, now double-click on the script to launch skype and your webcam should work ok...


#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

### Post by tkoopa on 2011-08-05
unfortunately that doesn't fix my problem ( same symptoms, trying to launch video has no effect) , thanks for suggesting it though

---

### Post by tkoopa on 2011-08-27
It's working again. It didn't work once and I was testing wrong when trying to fix it, skype testing call does not allow video.

---

