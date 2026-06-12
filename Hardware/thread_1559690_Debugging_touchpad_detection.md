---
title: "Debugging touchpad detection"
date: 2010-08-23
forum: Hardware
---

### Post by MountainX on 2010-08-23
Ubuntu is not recognizing the touchpad on my laptop. It sees it as an ImPS/2 mouse:
```
$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=12    [slave  pointer  (2)]
```


So I visited this page:
[https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection)
I got as far as this paragraph:
> 
If touchpad is not detected then following will appear. In this case the bug must be a kernel issue. **Name="ImPS/2 Generic Wheel Mouse"**Unfortunately, no further suggestions are given. OK, so it's a kernel issue... does that mean there is no solution for me?

---

### Post by IcarusR on 2010-08-24
Do you mean this bug

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/565543]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/565543")

If so then it is being looked into & when a fix is found it will be released as an update.

---

### Post by MountainX on 2010-08-24
> **IcarusR said:**
> Do you mean this bug

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/565543](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/565543)

If so then it is being looked into & when a fix is found it will be released as an update.

I did not actually refer to any specific bug. I was quoting from the Ubuntu wiki, which says "In this case the bug must be a kernel issue" and doesn't give any more help.

I did have a look at the bug you linked to. Unfortunately, that one doesn't suggest a work-around either.

The following attempt got me nowhere, as you can see:

```
$ sudo modprobe synaptics
**FATAL: Module synaptics not found.**

```

---

### Post by andreisun on 2011-03-04
So what did you do? My touchpad isn't working either and i've tried many things, but no solution yet...

Thanks,

Andrei

---

