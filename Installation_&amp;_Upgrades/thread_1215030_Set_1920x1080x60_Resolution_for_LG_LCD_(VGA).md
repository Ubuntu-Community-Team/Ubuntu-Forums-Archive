---
title: "Set 1920x1080x60 Resolution for LG LCD (VGA)"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by wojzeh on 2009-07-16
After installation of Ubuntu 9.04 (before I used 8.10) I got a problem with my LCD (LG W2442PA-BF) as a second monitor to my Toshiba laptop. The resolution should have been 1920x1080 as a maximum but was 1280x768 indeed.

With a little help of my friend and [this article]("https://wiki.ubuntu.com/X/Config/Resolution") I managed to add this absent line into xorg.conf file.

I am not sure about all these numbers in the following script for Terminal but it works as a charm.

[FONT="Courier New"][INDENT]sudo cvt 1920 1080 60 # 1920x1080 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz Modeline "1920x1080" 193.25 1920 2056 2256 2592 1080 1203 1209 1245 -hsync +vsync

sudo xrandr --newmode "1920x1080" 193.25 1920 2056 2256 2592 1080 1203 1209 1245 -hsync +vsync

sudo xrandr --addmode VGA "1920x1080"
[/INDENT][/FONT]

Now, you can easily set it in Display Setting utility.

---

### Post by ultimatePHIL on 2009-11-05
Hi, after typing in these 3 line the terminal tells me after the third line
"xrandr: cannot find output "VGA" "
Can u help me?

Thx anyway

---

