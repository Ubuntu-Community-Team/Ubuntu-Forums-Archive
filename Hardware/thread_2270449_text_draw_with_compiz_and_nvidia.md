---
title: "text draw with compiz and nvidia"
date: 2015-03-23
forum: Hardware
---

### Post by bolvan on 2015-03-23
Sometimes text in apps like gnome commander, wal commander, in freerdp session, etc
is not fully cleared or drawn.
For example, if I edit some text, press pagedown,pageup several times, delete some lines
then some portions of text that should not be left in editor are still present, they are not cleared
from the screen. If somehow i force window to redraw, for example take screen shot with PrintScreen,
I get correct view.
It happens only when
1) compiz is used as a display manager. no problem with metacity
2) nvidia proprietary drivers are used
It does not happpen on intel built-in graphics.

Anyone familar with the issue ?

My system is ubuntu 12.04 i386
nvidia 9600 GT

---

### Post by Vladlenin5000 on 2015-03-23
Hello and welcome.

Yes, I'm familiar with the issue. The solution may not be the ideal one in old machines like yours seem to be (why else you would be having a 32-bit OS in 2015?).

You need to install the CompizConfig Settings Manager (AKA CCSM) -> Available at software center, just search 'compiz'.
Then open it, go to Solutions and tick the "Force full screen redraws (buffer swap) on repaint" option.

---

### Post by bolvan on 2015-03-23
Actually my comp is not old, my OS is old. It was first installed on an old pentium-4.
Now its on core i7/4G RAM.
I'm too lazy to reinstall and reconfigure everything every 2 years. Will wait till 16.04 release.

Thanx, your advise helped. Full screen redraw happens not immediately (~after 1 sec), but its better than it was.
Slowdowns are insignificant.

Anyway, i'm still looking for a way to fix nvidia proprietary drivers behaviour.
May be some registrydwords, may be some glx fine tunes

Also I tested the problem on 14.04 livecd + nouveau. All OK.

---

### Post by tokyobadger on 2015-03-23
Read [this launchpad thread](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904) especially posts #358 and onward; the bug was in compiz. The workaround suggested by Vladlenin5000 was the only known solution until the recently updated compiz package which I believe is only released for Ubuntu 14.04 and newer.

What issues are you facing with the nvidia drivers?

---

### Post by bolvan on 2015-03-23
> **tokyobadger said:**
> 
What issues are you facing with the nvidia drivers?

Since compiz runs fine on everything but nvidia-proprietary I thought its nvidia bug.
But if the problem lies in compiz then ok, no problem, now I certainly know what to wait/look for.

Btw, any chance to backport latest compiz to 12.04 ?
I tried compiling. No errors during compilation but compiz doesnt work.
Main process loads core module and it does nothing.
I looked with strace. It even does not attempt read any configs or load any further libs.
System behaves like there's no window manager at all

---

### Post by tokyobadger on 2015-03-23
I'm a user not a dev - but I think it's fair to say the chances of an official backport to 12.04 would be slim as it's not a security related issue - could be wrong; with your upgraded hardware I would definitely consider an x86-64 install of a newer release and migrate your data

---

### Post by bolvan on 2015-03-23
This repo

[https://launchpad.net/~townsend/+archive/ubuntu/compiz-nvidia-refresh-test](https://launchpad.net/~townsend/+archive/ubuntu/compiz-nvidia-refresh-test)

contain fixed binary packages for different ubuntu versions including precise

Fix works perfectly ! No single glitch in redraw

---

### Post by tokyobadger on 2015-03-24
Great to here you found a solution and thanks for sharing, may help someone else in the future

---

