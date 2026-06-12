---
title: "Cannot get vesa driver 1024x768"
date: 2013-08-05
forum: Hardware
---

### Post by felichas on 2013-08-05
Hi,

[I have a problem with my nvidia card]("http://ubuntuforums.org/showthread.php?t=2165674"), and have to stick with vesa driver while I find a solution for it.
What I am doing is booting the system with the nomodeset kernel parameter 

```
$ grep nomodeset /etc/default/grub 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="#FF0000"]nomodeset[/COLOR]"
```

This works fine and /etc/X11/xorg.conf doesn't needed to exist.
But I can only choose 2 different resolutions:
 - 640x480
 - 800x600
And I rather use 1024x768 resolution instead. 
There are very many posts requesting the same, but none of the recepies I have tested so far (xorg.conf file) work for me. No matter what I have in xorg.conf, I always end up with vesa@800x600@60Hz if nomodetest is present, or with nouveau@1024x768@75Hz if nomodetest is not present at boot time (but then it freezes).
Am I missing something?

---

