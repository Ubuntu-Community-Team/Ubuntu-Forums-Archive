---
title: "Suspend to ram: (nx9010) blank screen"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by lorenzo on 2005-08-23
Hi,
I' trying to make my compaq nx9010 to go into standby. Well: it works! But when resuming my screen remains black and the cpu fans run very fast.....and nothing more. I have to reboot.....

I have an ati radeon igp 340 card (generic driver "ati", fgrlx does not work...).

I have no idea where to start on investigating the problem. 

Is there any log for suspend to ram? And for resumeelse activities??? I cannot find them. So I have no Idea where the problem stands: ati? X? something else???

can anyone help me?

Thanks,
Lo

P.D. I know similar questions have been asked all over again. I read a lot of posts but I'm still stuck at the starting point: my laptop does not resume...

---

### Post by nmincone on 2006-12-17
I'm running Edgy (6.10) on a nx9010 and have the same problem with both hibernation and suspension. Were you ever able to solve this? I'm still investigating the problem. I suspect the problem is a setting somewhere in
```
#sudo gedit /etc/default/acpi-support
```
One poster claims that after resuming from either setting a quick <cntrl-F1> to new TTY consol then <cntrl+F7> brought back the X GUI.

---

### Post by nmincone on 2006-12-21
As a followup I've installed the **suspend2** kernel ([see this thread]("http://www.ubuntuforums.org/showthread.php?t=284994")) and have had excellent results waking from suspend/hibernation for the first time. I still have a rouge driver that needs some assistance unloading (I think my wireless card). I am now able to wake but after a few moments I freeze. It's a good start though.

---

