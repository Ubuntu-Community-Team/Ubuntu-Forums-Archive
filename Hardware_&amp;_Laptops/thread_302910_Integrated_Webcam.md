---
title: "Integrated Webcam"
date: 2006-11-19
forum: Hardware &amp; Laptops
---

### Post by mariogl91@gmail.com on 2006-11-19
Hi, I have an HP dv6140us laptop that comes with an integrated webcam. I would like to know if there's some way to make it work.

I think the webcam is being detected because there's something called "USB 2.0 Camera" at the Device Manager. Maybe I just need to install the drivers?

Thanks.

---

### Post by mariogl91@gmail.com on 2006-11-19
I installed the Linux UVC drivers and tested the webcam with Ekiga. It worked when I selected V4L2 in the video plugin.

Now the question is, how do I make it work with other programs?

---

### Post by s_p_a_r_k_y on 2006-11-19
do you know the device name of it? you could use 
```
tvtime /dev/video0
```
or
```
mplayer /dev/video0
```

to see if they can find some video. Of course you would need to change /dev/video0 to whatever the correct device file is for that device.

---

