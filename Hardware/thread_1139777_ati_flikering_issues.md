---
title: "ati flikering issues"
date: 2009-04-27
forum: Hardware
---

### Post by pauloslf on 2009-04-27
hi,
i have installed jaunty on a laptop with a ati 36xx card, and i'm using an external monitor connected to it throw vga cable. the Monitor is a samsung syncmaster 2243nwx (1680x1050) 22".
my issue is that in some darker colours i notice the screen flickering (at least i don't notice that on clearer ones). i tried the same with other OS's (Windwos) and the monitor works just fine..
currently i'm using the opensource driver but the ATI ofitial one has the same results
what can be the issue?  refresh rate?


i'm really clueless :|

---

### Post by Threedays on 2009-04-27
There's problems with the ATI driver.  To get past the problem when running wine programs, you ctrl-alt-f6 to get to a terminal, then ctrl-alt-f7 to get back to desktop.  The flickering should then stop for that stage.

Not sure if the problem is fixed at the ATI level yet.  You'd think it would be major important.

The flickering happens when running wine programs and changing resolutions.

---

### Post by pauloslf on 2009-04-27
no, the issue happens everywhere.. i just need to have a darker color on the screen. eg. with firefox

---

### Post by kvdbreem on 2009-05-05
Hey all:
Yeah I've been having the same problems myself.  The ctrl+alt+f6 solutions seems to work sometimes.  I noticed that the flickering, once it's started, seems to get really bad if I try and get my computer to do some I/O against an external hard disk.  

I too have an ATI card and Ubuntu 904.  Monitor is pair of Samsung SyncMaster 2443BW.  Flickering is happening in the monitor that's carrying the extended display - so not the primary first monitor.  I can also see grainy lines when it's happening.

Refresh rate is fixed at 60 Hz according to my display settings.  

I have a feeling that what's happening here might have something to do with software rendering as opposed to hardware-based rendering due to poor Ubuntu 904 support in the ATI card...

---

### Post by pauloslf on 2009-05-07
guys.. i have the same issue on windows... so the issue is somewhere in hardware

---

### Post by executor on 2009-05-07
what you have sounds like a grounding problem, try running your laptop on battery, and se if the flikering is stil ther on the external monitor.

---

