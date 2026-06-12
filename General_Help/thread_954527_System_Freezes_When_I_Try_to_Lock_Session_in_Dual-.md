---
title: "System Freezes When I Try to Lock Session in Dual-Head Mode"
date: 2008-10-21
forum: General Help
---

### Post by swaters on 2008-10-21
I am running Kubuntu 8.04 on a Lenovo ThinkPad T60. I have an external Dell 19" Wide Screen Flat Panel (model E198WFPv) running off the video out as a secondary monitor. The primary monitor (laptop screen) is running at 1400x1050 res, and the secondary monitor is running at 1440x900. I am running an fglrx driver in dual-head mode, and when I select "Lock Session" from the K menu, the computer freezes. I have to do a hard reboot to bring it back.

I configured dual-head mode using the following aticonfig command:

aticonfig --initial=dual-head --screen-layout=left

This problem has existed since I got the monitor when I was using gutsy, and has lasted through several kernel upgrades. I suspect it is an fglrx problem. Any thoughts?

---

