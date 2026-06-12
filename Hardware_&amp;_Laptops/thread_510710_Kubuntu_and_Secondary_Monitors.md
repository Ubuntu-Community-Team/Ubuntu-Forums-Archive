---
title: "Kubuntu and Secondary Monitors"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by bsalt on 2007-07-26
Hey guys/gals,

I had Ubuntu installed for the past year or year and a half on my laptop, and now I switched over to Kubuntu Feisty (KDE4 :biggrin: is coming out and I still like Amarok more than Rhythmbox).

In Ubuntu I was able use dual monitors with Xinerama support in Ubuntu. *However*, in Kubuntu, there is no default /etc/X11/xorg.conf file at first. But what I saw was that in System Settings, there is a nice little tool to configure monitors and resolutions and such. So I used that tool to add a second monitor for use with my laptop's screen and rebooted.

Kubuntu would not boot up. I found out (using my *Windows* box) that I needed to type "sudo dpkg-reconfigure xorg-server" to fix the problem, and it worked. It also added the much needed xorg.conf file.

I've followed some of these threads to enable multiple monitors by editing the xorg.conf file, and every time it resulted in me breaking the X server. In Kubuntu, am I editing the wrong file?

**But I still can't seem to even get a second display to work. What's up with this?**

**Does Kubuntu use X.org, or XFREE86 by default?**

---

### Post by bsalt on 2007-07-26
Nevermind, I found the page I needed! (hopefully)

I'll let you know if it works.


Buut, for those curious, the page is at:
[https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)


And apparently, X.org doesn't install the xorg.conf file at first. So, running the following command is a must.
```
"sudo dpkg-reconfigure xorg-server"
```

---

### Post by bsalt on 2007-07-27
Ok, so that how-to for some reason didn't work the first time I tried it... (with the same previous problems)... and then I tried it again, and it works. However... Xinerama does not work well at all. The windows will not drag over, leaving black squares on the second monitor, rendering it useless. However, the Clone method works perfectly; I virtually have two machines. I can run a program on the second screen without seeing it or recieving any notification from it on the first screen. It works nicely in that aspect, but the extended desktop function is not working for me.

Any ideas?

---

