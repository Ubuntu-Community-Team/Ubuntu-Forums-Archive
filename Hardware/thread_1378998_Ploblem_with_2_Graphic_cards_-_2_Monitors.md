---
title: "Ploblem with 2 Graphic cards - 2 Monitors"
date: 2010-01-12
forum: Hardware
---

### Post by jmiggal on 2010-01-12
Hi everybody!

I am trying to make work two graphic cards on a P-IV computer under Ubuntu 9.10 which are:

[LIST=1]
[*]S3 Trio 64V+ 86c765
[*]ATI 264VT
[/LIST]
The output of lspci command is:

jomg2@jomg2-desktop:~$ lspci | grep VGA
05:04.0 VGA compatible controller: S3 Inc. 86c764/765 [Trio32/64/64V+] (rev 53)
05:09.0 VGA compatible controller: ATI Technologies Inc 264VT [Mach64 VT] (rev 40)

which I think is correct (both cards are detected). As I am using Ubuntu 9.10 there is no xorg.conf archive but I edited it entering to the system as text mode and executing "Xorg -configure". The generated archive is attached to this post. It looks fine since it has two device, two monitor, and two screen sections.

Both of the graphic cards work ok when using them by separate. My problem is that using them at the same time I do not get any signal on my ATI card (monitor says: No VGA signal). Furthermore, I installed the gradr GUI and only one monitor (one output) is detected. My first idea is to manage both monitors with this tool (gradr).

My goal is to show an application to load multimedia content on one monitor. On the other monitor multimedia content will be displayed (hidding the application showed on the first monitor)

Can you help me, please?

---

