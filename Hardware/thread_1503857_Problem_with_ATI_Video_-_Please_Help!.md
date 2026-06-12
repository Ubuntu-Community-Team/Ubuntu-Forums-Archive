---
title: "Problem with ATI Video - Please Help!"
date: 2010-06-07
forum: Hardware
---

### Post by Yehudah on 2010-06-07
I have installed Ubuntu 10.4 LTS onto my Dell 1536 AMD laptop. I've been struggling for two weeks with several issues. I'm not a newbie to Ubuntu, but I've become very frustrated with this version and I'm close to needing to go back to W7 (yeck).

I have surfed these and other forums for almost two weeks now and have used workarounds and supposed fixes that don't work. Here is one of my issues:

I have no 3D video. I activated the ATI drivers that came with this distro and it worked fine, until I rebooted. Then the video defaulted to the original setting (which work but are only 2D). I have d/l'd drivers, uninstalled, installed, reinstalled the broken packages, yada yada yada, and now I am unable to active the drivers at all. Not very happy with that.

Can anyone assist me with this?

---

### Post by Crafty Kisses on 2010-06-07
What are the results of the following?
```
glxinfo
```

---

### Post by Yehudah on 2010-06-07
yehudah@yehudah-laptop:~$ glxinfo
name of display: :0.0
Segmentation fault

It isn't what I expected, but I don't have the ATI driver installed any longer... it gives me too much grief.

Any hints?

---

### Post by Crafty Kisses on 2010-06-09
Hello,

Sorry for the late replies, I've been busy as of late. Anyway, I might need some more logs to see what's going on. Can you please post the results of the following?
```
dmesg
/var/log/Xorg.0.log

```
Then see if the correct modules are running, because I see a lot of recurring problems with the ATI cards similar to this one, so can you please also post the results of the following?
```
lsmod | grep -i fgl
```
Thanks, and I'll try to help you further.

---

