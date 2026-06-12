---
title: "Don't know where to start!!! Floppy drive help!!!"
date: 2009-01-02
forum: Hardware
---

### Post by johnson8707 on 2009-01-02
So I've been trying to figure out linux/ubuntu for a little while now and its not going too well.

I've got my system up and running. (so to speak) I made my Linux box from scratch. I installed a floppy drive and CD-ROM drive. I know the CD-ROM drive is functioning (how I installed Ubuntu) and I believe the floppy drive is functional also.

I get this error message anytime I try to look at the Places>Floppy Drive:
[INDENT]**Unable to poll Floppy Drive for media changes**

Cannot invoke CheckForMedia on HAL: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
[/INDENT]

CAN SOMEONE TRANSLATE THIS?? And also tell me how to fix it if you can. :)

Thanks!

---

### Post by cariboo on 2009-01-02
Dependoing on which version you are running, the floppy module may not be loaded. To see if the floppy module is loaded in an Applications-->Accessories-->Terminal type:

```
lsmod | grep floppy
```

If you don't get anything printed out on screen, you need  to load the floppy module. To do this ins the same terminal type:

```
sudo modprobe floppy
```

If the module was loaded properly, you won't see anything echoed back.

You should be able to use  your ancient :) floppy drive, once the module is installed.

Jim

---

### Post by johnson8707 on 2009-01-02
Ok. I did that and it responded:
[HTML]floppy      59588  0[/HTML]


What does that mean? Is that good?

---

### Post by Sef on 2009-01-02
Check out this [thread]("http://ubuntuforums.org/showthread.php?t=911858").

---

