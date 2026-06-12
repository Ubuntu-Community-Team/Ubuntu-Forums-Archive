---
title: "Webcam Permissions Issues in /dev/video0"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by kzetts on 2009-10-29
Hey guys,

I just upgraded from 9.04 to 9.10, and everything in the change over worked smoothly, except for one thing: anytime I run a program that accesses the webcam, nothing is displayed.

So I did a little digging, and it's a permissions issue.  For example, if I run 'gksudo cheese' I'm able to view my webcam, but not with 'cheese'.

I've added myself to the video group, and made sure that my user profile is able to access video hardware, but the issue is still not resolved.  Any ideas, hints or solutions?  They'd be greatly appreciated.

Thanks.

---

### Post by sisco311 on 2009-10-29
did you log out and log back in after adding your user to the video group?

what's the output of:
```
ls -al /dev/video*
```

---

### Post by kzetts on 2009-10-29
I logged out and logged back in since then.

The output of ls -al /dev/video* is

```
crw-rw----+ 1 root video 81, 0 2009-10-29 21:53 /dev/video0
```

---

### Post by trpnblies7 on 2009-11-01
I'm having the same issue. My webcam is only working when I open programs as root. How do I fix this?

---

### Post by branque on 2009-11-12
Have same problem using Ubuntu 9.04, done what been suggested above, found a temp. solution each time I start my computer, to write in console

sudo chmod 777 /dev/video0

Afterwards webcam works fine in skype, msn, cheese software. Havent found a permanent solution yet, still looking.

---

### Post by trpnblies7 on 2009-11-12
I solved the problem, though I don't know if my issue was the same as everyone else's.

My issue was this: [http://ubuntuforums.org/showthread.php?t=1316498](http://ubuntuforums.org/showthread.php?t=1316498)

I solved it by editing /etc/rc.local to create the file on boot, and then I placed a script in /etc/rc0.d to delete the file when I shutdown my computer. Now everything works just as it did in Jaunty for me.

---

