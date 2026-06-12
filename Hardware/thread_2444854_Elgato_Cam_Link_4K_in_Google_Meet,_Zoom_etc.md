---
title: "Elgato Cam Link 4K in Google Meet, Zoom etc"
date: 2020-06-05
forum: Hardware
---

### Post by johanhalse on 2020-06-05
After a bunch of fiddling I just got this working, so figured I'd post the magic incantation here for posterity, as well as how I cracked it. I have an Elgato Cam Link 4K hooked up to a Panasonic Lumix DSLR, so I get that beautiful soft focus in remote meetings. It worked nicely in MacOS but I didn't have much luck in Ubuntu: programs would detect /dev/video0 and /dev/video1 but it would just never work. FFmpeg said something about corrupted bytes.

The camera DID work fine in OBS Studio though. So I started OBS from the command line and took note of the stuff it spewed in the log, most notably "50fps", "yuy", and "1920x1080". I googled ffmpeg's various pixel formats and it had one called "yuyv422".

Next thing I got from another forum: install v4l2loopback. This creates a dummy video capture stream that you can pipe stuff to. So the magic incantation is this:

```
sudo modprobe v4l2loopback
ffmpeg -f v4l2 -framerate 50 -pix_fmt yuyv422 -video_size 1920x1080 -i /dev/video0 -f v4l2 -vcodec rawvideo -pix_fmt yuv420p /dev/video2
```

This makes ffmpeg read from the /dev/video0 stream with the options I got from OBS, and pipes it to our new dummy stream in the "yuv420p" format (which seems a little bit more standard). Now I can pick that dummy device and use it as expected!

Hope this helps somebody from the future :)

---

### Post by adamgleave on 2020-10-25
Thanks for posting the solution -- this helped me out!

In case anyone else is running into this problem, I made a Python script to automate launching the relevant ffmpeg command in the background [here]("https://github.com/AdamGleave/elgato-camlink-workaround").

---

### Post by bdrung2 on 2021-03-25
There is a bug in the Cam Link 4K firmware which breaks all pixel formats except the  first one. I developed a quirk to fix the buggy firmware and submitted  it to the upstream Linux: [https://lore.kernel.org/lkml/20210325213458.51309-1-bdrung@posteo.de/](https://lore.kernel.org/lkml/20210325213458.51309-1-bdrung@posteo.de/)

So once this patch is accepted, backported to older kernel released, and included in the Ubuntu kernel this workaround is not needed  any more.

---

### Post by bdrung2 on 2021-07-20
The fix was accepted upstream: [COLOR=#4C4C4C][FONT=&amp][commit 4c6e0976295add7f0ed94d276c04a3d6f1ea8f83]("https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=4c6e0976295add7f0ed94d276c04a3d6f1ea8f83")

This fix was also backported to the stable releases. The fix is included [/FONT][/COLOR][COLOR=#4C4C4C][FONT=&amp]in:
[/FONT][/COLOR]
[LIST]
[*][COLOR=#4C4C4C][FONT=&amp]4.4.276[/FONT][/COLOR] 
[*][COLOR=#4C4C4C][FONT=&amp]4.9.276[/FONT][/COLOR] 
[*][COLOR=#4C4C4C][FONT=&amp]4.14.240[/FONT][/COLOR] 
[*][COLOR=#4C4C4C][FONT=&amp]4.19.198[/FONT][/COLOR] 
[*][COLOR=#4C4C4C][FONT=&amp]5.4.134[/FONT][/COLOR] 
[*][COLOR=#4C4C4C][FONT=&amp]5.10.52[/FONT][/COLOR] 
[*][COLOR=#4C4C4C][FONT=&amp]5.12.19[/FONT][/COLOR] 
[*][COLOR=#4C4C4C][FONT=&amp]5.13.4[/FONT][/COLOR] 
[*][COLOR=#4C4C4C][FONT=&amp]5.14-rc1
[/FONT][/COLOR] 
[/LIST]
[COLOR=#4C4C4C][FONT=&amp] This bug tracks the backport in Ubuntu: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1932367](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1932367)
[/FONT][/COLOR]

---

