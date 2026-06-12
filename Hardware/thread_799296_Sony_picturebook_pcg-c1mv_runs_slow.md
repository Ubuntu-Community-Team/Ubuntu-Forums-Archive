---
title: "Sony picturebook pcg-c1mv runs slow"
date: 2008-05-18
forum: Hardware
---

### Post by HawleySmoot on 2008-05-18
Hey all,
Just bought an old Sony off a friend and figured I'd replace xp with Ubuntu. The installation goes off without a hitch, but when I get to the desktop and start trying to actually use it, I realize that it's unbearably slow(XP ran better :(). I check the system monitor and the cpu is at 50-100 percent usage all the time. 'Whatever', I say to myself, 'I'll install Xubuntu'. Install xubuntu, get to the desktop, practically no change in performance. Cpu usage is still very high. After fooling around alittle bit I discovered that "indirect rendering: yes". I concluded that the cpu was being taxed because the graphics card wasn't working properly.So I tried to install the ati drivers, but only succeeded in making the computer run in low-graphics mode. If anyone has experienced this or has any idea what the problem might be I'd really appreciate some help, thanks.
specs:
Crusoe 773 mhz
380 some megs of ram
20 gb hd
Ati mobility radeon -m(though glxinfo reports it as an Ati mobilty m6 ly)

---

### Post by HawleySmoot on 2008-05-19
bump

Edit: I tried to install the ati drivers by following these two guides. [http://ubuntuforums.org/showthread.php?t=138343](http://ubuntuforums.org/showthread.php?t=138343)
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
The second one mentions that there might be a problem with the residual mesa drivers. This seems like my problem, as when I do fglrxinfo it says mesa. However, I've tried all the options for removing the drivers suggested by the guide and still no luck.

---

### Post by HawleySmoot on 2008-05-20
Bump!

---

