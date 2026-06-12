---
title: "Trackpoint &quot;press to click&quot;"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by nanophobic on 2007-06-09
I have a fresh feisty install on a Thinkpad R60E . Would anyone happen to know of how to enable "press to click" for the trackpoint? i.e. make the tapping of trackpoint emulate a left click.

Is it possible with the drivers that Ubuntu provides?

I've checked thinkwiki, but they talk about installing a thirdparty driver that involves patching the kernel. I'm uncomfortable using that route, since I'm not sure if I would have to repeat the process everytime a kernel upgrade occurs.

thanks in advance!

---

### Post by 444 on 2007-06-09
echo -n 1 > /sys/devices/platform/i8042/serio1/serio2/press_to_select 

On my T40 though.

---

### Post by nanophobic on 2007-06-09
Thanks 444!

I just managed to enable trackpoint press_to_select.

For some weird reason, my trackpoint settings are located in

/sys/devices/platform/i8042/serio1/input:mouse2/device/

instead of

/sys/devices/platform/i8042/serio1/serio2/

and now I have managed to enable trackpoint "press to click" along with the ability to adjust trackpoint parameters like sensitivity etc! 

oh btw, if it helps, my kernel version is 2.6.20-16 and my machine is R60E

thanks again for your response!

---

### Post by mezhaka on 2007-12-05
on my Thinkpad x31 the file location is:
/sys/devices/platform/i8042/serio1/press_to_select

---

