---
title: "suspend/resume, detecting trackpad at wrong event?"
date: 2006-06-23
forum: Hardware &amp; Laptops
---

### Post by jerwarren on 2006-06-23
I've noticed recently that when suspending and resuming, my trackpad would occasionally stop working, requiring a ctrl-alt-backspace to get it working again.  Now since upgrading to dapper, it does it pretty consistently, and so I've been trying to figure out what the problem is.

After much experimenting and looking through logs, I've discovered that the trackpad (and mouse) are being detected at ever increasing input #'s.  From the logs:

```

Jun 23 09:54:56 localhost kernel: [17237826.612000] input: PS/2 Mouse as /class/input/input27
Jun 23 09:54:56 localhost kernel: [17237826.636000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input28

```

A half hour ago at the beginning of my testing those input numbers were 15 and 16 respectively.  Obviously this isn't the same as the /dev/input/event2 (where the trackpad lives), but are they related?  My theory is that for some reason suspend/resume isn't properly associating the new input with the proper event.

Is this a possibility?

---

