---
title: "8800 GTS 320 MB X-server Problem"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by srudes2 on 2007-06-26
I pretty much installed the whole nvidia driver from the nvidia website for ubuntu successfully.
I installed it when the x-server is not running. Then I used the command: sudo /etc/init.d/gdm restart
Then I got the login screen and I even installed beryl successfully...everything looked alright until I restarted the computer. It gave me the error: 
```
Failed to start the x server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
```
.... yes.....
```
Blablabla
Error: API mismatch: this NVIDIA driver component has version 100.14.11, but the NVIDIA kernel module's version does not match. Please make sure that the kernel module and all NVIDIA driver components have the same version
NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
NVIDIA(0):       that there is a supported NVIDIA GPU in this system, and
NVIDIA(0):       that the NVIDIA device files have been created properly.
NVIDIA(0):      Please consult the NVIDIA README for details

```
Now I can get the graphics to show up only when I reinstall the nvidia driver and do:  sudo /etc/init.d/gdm restart
That's a bit too much work to do for every restart

Thank you and I hope to get a response asap:D

---

### Post by srudes2 on 2007-06-26
Sorry guys... apperently the nvidia drivers on nvidia.com aren't the newest.
Go there:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14&page=2&order=desc](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14&page=2&order=desc)
To get the newest.
Whee my problems are solved thnx anyway!

---

### Post by diepruis on 2007-06-30
I'm having the same problem you had. Could you please clarify what you meant in the above post? I went to check the link, but the version provided there is exactly the same as the version provided by nVidia.

---

