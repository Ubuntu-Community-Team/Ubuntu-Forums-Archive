---
title: "Mouse and alt+tab stops working on Toshiba Tecra M10 running ubuntu 9.04 and 10.04"
date: 2010-05-11
forum: Hardware
---

### Post by sahoo on 2010-05-11
I have had this problem using Ubuntu 9.04 and I see it with 10.04 as well. In 9.04, I had seen it using both kde as well as gnome. The problem isthat  occasionally my mouse and alt-tab stops working. It appears all mouse events are tied to the current active window only. I can't change active window using alt-tab as well. But, I can create a new gnome-terminal via Alt+F2. If I kill the window by going to a terminal, then focus shifts to the next window, but again the same problem. So, I have to reboot the system. I understand I am not providing sufficient detail here for an expert to help, but please let me know what details you need; I shall try to provide them. Here is the output of uname:

**Linux Sahoo 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux**

Thanks in advance.

---

### Post by ddalex on 2010-06-29
I have the same problem with a Dell Optiplex desktop, the mouse works only until I open a window. Alt-tab also stops working. 

I'm running the most up-to-date Ubuntu, and just found out that the bug happens only on kernel 2.6.32-23-generic, on 2.6.32-23-generic, it doesn't happen on 2.6.32-22-generic.

I'm trying to debug it but if anyone finds a solution/workaround please say so :).

---

### Post by nullvariable on 2010-07-27
I'm also experiencing this on my desktop, tested keyboards and mice but neither of those seem to be the issue. I'm running 10.04 with the latest kernel, 2.6.32-24.

Any thoughts? suggestions? troubleshooting tips? services I can restart?

Thanks!

---

### Post by biturica on 2011-02-11
This also happened to me on a Compaq Presario CQ60-215DX laptop, running Lucid 64bit, Gnome 2.x edition.

Uname output is:
Linux cq60 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011 x86_64 GNU/Linux

I managed to open the system monitor with my keys. The only thing that  jumped out at me (and I don't know if it means anything at all), but one  of my Chromium browser tabs was shown the waiting channel  "__skb_recv_datagram".

I ended up just hitting control-alt-del to restart.

edit 01:
I think shortly before the freeze I had gone into my keyboard settings  to disallow pointer control via the keyboard (I had set this before, as  otherwise my numeric keypad is useless, but somehow the setting got  reverted without me opening any preferences dialogs). I don't know if  this is related in any way.

---

### Post by robobart on 2011-02-27
Same problem on a Dell e4300.

---

### Post by dwiel on 2012-01-12
This has been happening to me too.  I've got a Thinkpad T420s running 11.04.  Most of the time I can recover from it, this most recent time killing Virtual Box solved the problem...

---

