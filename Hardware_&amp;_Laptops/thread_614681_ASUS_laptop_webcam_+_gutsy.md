---
title: "ASUS laptop webcam + gutsy"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by occhiso on 2007-11-16
Hi,

I was trying to get my built in webcam in my laptop to work under ubuntu, but cant seem to find a solution.

Some articles in these forums refer to a "syntek" camera, but when i do a lsusb, i get this, instead of "syntek":
```
ALi Corp. Video Camera Controller
```

After googling this, i only found partial projects,etc.
I installed "camorama" from the repositories and get this message:
```
Could not connect to video device (/dev/video0)
Please check connection.
```

Any help would be appreciated,
thanks,

occhiso

---

### Post by tinycamp on 2007-11-16
what module are you using ??? stk11xx ??, have u tried xawtv, or maybe ekiga ?

cc

---

### Post by occhiso on 2007-11-17
Im sorry, im new to this sort of stuff.
I tried xawtv, and I get this message when I try to run it:
```
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
WARNING: Your X-Server has no DGA support.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

```
Which is the same sort of message from camorama.

---

### Post by jespdj on 2007-11-17
> **occhiso said:**
> After googling this, i only found partial projects,etc.
I installed "camorama" from the repositories and get this message:
I get the same with the webcam in my Dell XPS M1330 laptop. The cause of this is that the webcam is only supported by V4L2 (Video4Linux 2), while Camorama only supports the older V4L.

Try a different webcam program, for example Cheese (it's in the Ubuntu repository and will show up in Applications / Accessories after installation).

If that's not the problem then check if your webcam is really /dev/video0. Maybe it has a slightly different device name, such as /dev/video or /dev/video1. Open a terminal and type
```
ls /dev
```
to see which device names exist on your computer.

---

### Post by occhiso on 2007-11-17
Thanks for your reply,
I tried ```
ls /dev 
``` and couldn't find anything that resembled a webcam :confused:

I dont know how this sort of stuff works on linux, but under windows id say I need to install a driver... but im pretty certain my laptop didnt come with a linux driver in the box (or a stand alone windows driver for that matter)

---

