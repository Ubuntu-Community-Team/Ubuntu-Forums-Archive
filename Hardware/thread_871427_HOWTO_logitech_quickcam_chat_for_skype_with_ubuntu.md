---
title: "HOWTO logitech quickcam chat for skype with ubuntu gutsy and skype II (Dark image)"
date: 2008-07-26
forum: Hardware
---

### Post by Davidde_madrid on 2008-07-26
After read this post [http://ubuntuforums.org/showthread.php?t=651375]("http://ubuntuforums.org/showthread.php?t=651375") I see that the images that come out of my webcam was pretty dark well I found not a solution but something nearly to it in this post [http://nadirdome.blogspot.com/2007/12/installazione-logitech-quickcam-for.html]("http://nadirdome.blogspot.com/2007/12/installazione-logitech-quickcam-for.html").
It's in italian but the poster is talking to change the /etc/modprobe.d/options file adding some parameters.
For my problem was enough to add the line:
options gspca force_rgb=0 GRed=400 GGreen=420 GBlue=420 autoexpo=0

Hope it would help somebody

PS. I tried to add this post to the main one but it was blocked by administrators

---

