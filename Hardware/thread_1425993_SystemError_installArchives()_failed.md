---
title: "SystemError: installArchives() failed"
date: 2010-03-09
forum: Hardware
---

### Post by Cleveland Rock on 2010-03-09
When I try to activate "NVIDIA accelerated graphics driver (version 195)" in Hardware Drivers, I get the error message "SystemError: installArchives() failed". I'm kind of a n00b with Ubuntu, so I don't know what other information to give you. Any ideas?

```
clevelandrock@Centurion:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
```

---

### Post by Cleveland Rock on 2010-03-10
Bump.

---

### Post by Cleveland Rock on 2010-03-12
Pretty please?

---

### Post by Cleveland Rock on 2010-03-12
Pretty please with sugar on top?

---

### Post by xhalarin on 2010-03-15
I had a similar problem with the nvidia 185 driver today.  It was caused by messing around with the files driver manually.  I managed to resolve the issue by using the jockey-text command from the command line.

If you go to a terminal window and type this:
jockey-text -l

You can see all of the proprietary drivers that are installed and whether they are enabled or disabled.

Run this to refresh your jockey database:
jockey-text -u -c 

Then try this:
jockey-text -e xorg:nvidia-195
(replace xorg:nvidia-195 with whatever the first part of the driver name is when you used the -l parameter if it's different)

If this doesn't fix you up, I thought this thread had some good information for other commands to look at:
[http://art.ubuntuforums.org/showthread.php?t=1115079&page=2](http://art.ubuntuforums.org/showthread.php?t=1115079&page=2)

Good luck.

---

### Post by calande on 2010-04-07
Thanks! This solved my problem :)
I suspect also another instance of Synaptic running caused it.

---

### Post by tommywalsh on 2010-05-14
I just wanted to drop in and second this.  I had the same problem, same error message.  Same error message even when using jockey-text.  It was definitely a problem with Synaptic running.  Closing Synaptic solved the problem.

Thanks!
Tom

---

### Post by John Hollar on 2010-08-12
I would also like to mention that I am pants-on-head-retarded and attempted to install my nvidia drivers with Synaptic running. Oops!

---

### Post by Rathalos on 2010-08-13
> **John Hollar said:**
> pants-on-head-retarded  

Yes. Same problem, same fix for me.

---

### Post by im_riley on 2010-09-23
> **tommywalsh said:**
> I just wanted to drop in and second this.  I had the same problem, same error message.  Same error message even when using jockey-text.  It was definitely a problem with Synaptic running.  Closing Synaptic solved the problem.


This worked for me as well. Thanks. :D

---

### Post by thefinn12345 on 2010-12-24
Unfortunately, it hasn't worked for me. I get the exact same error on command line as I do in the applet. Any help ?

---

### Post by angvzp0x on 2011-10-21
I got this error when I had the Synaptic package manager open in the background

---

