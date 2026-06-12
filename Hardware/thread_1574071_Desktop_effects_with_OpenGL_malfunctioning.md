---
title: "Desktop effects with OpenGL malfunctioning"
date: 2010-09-13
forum: Hardware
---

### Post by alleluia20 on 2010-09-13
Hello,

I think this is a kernel issue, I have already submitted the bug [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/637579](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/637579), but I am posting here as well just in case this is an xorg or a kde issue, or in case it is still a kernel issue but you can help me :-)

Let me start by saying that **I am using maverick**.

In Kubuntu maverick, kde desktop effects using OpenGL are a disaster.  For some windows, such as skype, they seem to work OK (even the woobly  effect). For others, such as konsole, the woobly effect shows a lot of  stranger frames. Windows with GTK applications appear completely broken  (only a few bits are displayed). And it is not only about individual  Windows: switching to the desktop or another virtual desktop shows a lot  of frames of the running applications.

 My graphic card is:
VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

 I have no file /etc/X11/xorg.conf. If I run Xorg -configure, I get the output attached in my bug report linked above, which reads
(EE) intel(0): No kernel modesetting driver detected

 And, if you try to start the server with the created xorg.conf.new,  you get nothing but a big cross that I think it is the mouse pointer of  X.

 The desktop effects used to work, with OpenGL, in Ubuntu 10.04  (although I used to have the known kernel panics related to the intel video  driver, also with the desktop effects disabled).

Any ideas? Thank you very much in advance

---

### Post by realzippy on 2010-09-13
Did it work in 10.04 without disabling KMS ??

---

### Post by alleluia20 on 2010-09-13
> **realzippy said:**
> Did it work in 10.04 without disabling KMS ??

Thank you for the reply. Yes, it used to work in 10.04, but how, honestly, I do not know. I did not do anything in the kernel or in xorg.conf (in case that file still existed in 10.04); if you can remember the default options in 10.04, we can have the answer to your question :-)

---

