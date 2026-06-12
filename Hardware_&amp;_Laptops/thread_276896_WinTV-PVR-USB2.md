---
title: "WinTV-PVR-USB2"
date: 2006-10-13
forum: Hardware &amp; Laptops
---

### Post by brottman on 2006-10-13
Last desperate attempt before I give up. I have Edgy on my laptop with all the updates. I've tried for a week to get my Hauppauge WinTV-PVR-USB2 tuner to work. Heres what I've done so far:

1. I compiled Mike Isleys latest driver and put pvrusb2.ko into /lib/modules/2.6.17-10-generic.
2. I put the 2 firmware files (v4l-pvrusb2-29xxx-01.fw) and (v4l-cx2341x-enc.fw) into /lib/firmware.
3. depmod -a
4. modprobe pvrusb2
5. reboot.

The only thing I can accomplish so far is gettting mplayer to bring up a single channel by running ```
mplayer /dev/video0
``` ... but I don't know how to control it or change channel or anything.

When I run TvTime it just comes up with a blue screen and says "Incorrect parameter.." or something similar. XawTV just outputs about 5 or 6 lines of error messages.

In the best interest of my mental health... someone PLEASE help me!

Brian

---

