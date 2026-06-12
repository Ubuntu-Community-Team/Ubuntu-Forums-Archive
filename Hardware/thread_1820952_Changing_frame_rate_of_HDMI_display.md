---
title: "Changing frame rate of HDMI display"
date: 2011-08-08
forum: Hardware
---

### Post by ericsp on 2011-08-08
My HDMI display starts flickering when using the standard 1280x1024 mode. I can solve this issue by entering in the command line:
```
sudo xrandr --output HDMI1 --mode 1280x1024 --rate 60
```
How do I make changes to my xorg.conf or otherwise, to make this solution permanent? I am using Oneiric (Ubuntu 11.10 alpha 3).

Thanks.
Eric

---

