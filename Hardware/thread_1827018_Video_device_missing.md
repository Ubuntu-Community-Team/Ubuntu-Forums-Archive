---
title: "Video device missing"
date: 2011-08-17
forum: Hardware
---

### Post by Caspinol on 2011-08-17
Hello all,

I am trying to record a video using XAWTV but it seems that video0 device is missing from the /dev list. I appreciate any help in sorting out the problem. 

Here is the output from ```
lspci | grep VGA
``` command:
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]

```

Running ```
xawtv -c /dev/video
``` gave this output:

```
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.38-10-generic)
xinerama 0: 1920x1080+0+0
can't open /dev/video: No such device or address
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video: No such device or address
v4l2: open /dev/video: No such device or address
v4l: open /dev/video: No such device or address
no video grabber device available

```
Thanks in advance for the help

---

### Post by Caspinol on 2011-08-18
anybody have any idea??

---

### Post by grahammechanical on 2011-08-18
I guess it means that you do not have a TV tuner card in your machine. Or, it is not recognized by the Linux kernel. Which is it?

Are you aware of this site?

[http://www.linuxtv.org/wiki/index.php/Special:Categories]("http://www.linuxtv.org/wiki/index.php/Special:Categories")

Information about devices that work or do not yet work in Linux.

Regards,

---

