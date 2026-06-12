---
title: "Fujitsu Laptop Skype Upside-Down video"
date: 2014-05-03
forum: Hardware
---

### Post by Sana_Sultan on 2014-05-03
Hello,

I have installed Ubuntu 14 and Skype 4.2. While I go in Options->Video Devices, I see upside down images in the video screen. Even I am unable to start a video call. Please help.

---

### Post by Sana_Sultan on 2014-05-03
> **Sana_Sultan said:**
> Hello,

I have installed Ubuntu 14 and Skype 4.2. While I go in Options->Video Devices, I see upside down images in the video screen. Even I am unable to start a video call. Please help.


Solved:
In Terminal:

[COLOR=#FF0000][FONT=Lucida Grande]sudo [/FONT][/COLOR][COLOR=#000080][FONT=Lucida Grande]gedit[/FONT][/COLOR][COLOR=#FF0000][FONT=Lucida Grande] /usr/local/bin/skype[/FONT][/COLOR]

Paste the following in the blank file:
[COLOR=#404040][FONT=Verdana]#!/bin/bash[/FONT][/COLOR]
[COLOR=#404040][FONT=Verdana]LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype[/FONT][/COLOR]
[COLOR=#3A453B][FONT=Lucida Grande]
Save the file and close it.[/FONT][/COLOR][COLOR=#3A453B][FONT=Lucida Grande]
Now to make the file executable, copy and paste the following line into Terminal.[/FONT][/COLOR][COLOR=#3A453B][FONT=Lucida Grande][COLOR=#FF0000]sudo chmod a+x /usr/local/bin/skype[/COLOR][/FONT][/COLOR]

---

