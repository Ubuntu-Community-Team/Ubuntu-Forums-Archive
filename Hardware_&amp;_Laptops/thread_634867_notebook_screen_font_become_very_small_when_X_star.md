---
title: "notebook screen font become very small when X started with external display plugged"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by zhangweiwu on 2007-12-08
Dear all

I am not sure if this is a hardware problem, but a software problem that only happen with notebook. I have Ubuntu 7.04 running on my notebook.

If the external display is plugged when X starts, the screen font is extremely small (not readable).

If the external display is not plugged when X starts, the screen font is normal, but plug in external display afterwards, the external display do not have video signal (is blank), only internal flatpanel display has signal.

I have made a screenshot of when X starts without external display:
[IMG]gopher://sdf.lonestar.org/I/users/weiwu/flatpanel_display.png[/IMG]

And I made another screenshot when X started with external display, the difference is obvious.
[IMG]gopher://sdf.lonestar.org/I/users/weiwu/external_display.png[/IMG]

I am not sure how this happened. Can it because the system tries to set font size to 9point, which is probably 12 pixels on flatpanel but is only several pixel on external display (which is a projector)?

how can I fix this? My audience cannot see the text when I am using projector, if it is only 5 pixel size for each character.

---

### Post by zhangweiwu on 2007-12-09
Now I am able to answer my own question. I followed this guide:
[http://gentoo-wiki.com/HOWTO_Xorg_and_Fonts](http://gentoo-wiki.com/HOWTO_Xorg_and_Fonts)
Where it suggested me to specify DisplaySize

I use exactly the suggested values in this guide and my screen font become readable again.

---

