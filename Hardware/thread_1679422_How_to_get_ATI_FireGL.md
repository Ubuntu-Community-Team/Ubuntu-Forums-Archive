---
title: "How to get ATI FireGL?"
date: 2011-02-01
forum: Hardware
---

### Post by W-Unit on 2011-02-01
Hi there,

A few days ago, I installed Ubuntu on my desktop, which has a Radeon HD 5850 GPU.
Video performance was pretty terrible (considering it's a high-performance GPU) until I was able to get ATI FireGL up and working, thanks to some help from you folks :)

Now I've just gotten a brand new Asus Eee PC 1215T netbook (which has a Radeon HD 4250 GPU if I'm not mistaken) and I'm having similar problems. With the default drivers perfromance is -pretty good-, but based on reviews and advertisements online, it should be capable of 1080p playback, which it currently isn't, and I suspect this is because I can't get FireGL working. Presently, 720p video is moderately choppy and drives CPU usage up to about 96%, while 1080p is severely choppy and maxes out the CPU.
Getting FireGL on the desktop was a process of much trial and error, and thus I can't really replicate it as I installed and uninstalled so much stuff along the way until it finally worked. Here is the thread in which the procedures are described which got FireGL working on the desktop (look for the post by tcrapper):
[http://ubuntuforums.org/showthread.php?p=10416103](http://ubuntuforums.org/showthread.php?p=10416103)

When I tried these procedures on the netbook, the shell script appeared to run fine, but at the end I was given a handful of error messages about not being able to locate some config file... I presume this problem is supposed to be solved by executing the **aticonfig -f --initial** command as described in that thread, however when I try to run this command (I must first navigate to **/usr/lib/fglrx/bin**), I get this message:
```
Unable to open /etc/ati/control, please reinstall the driver.
./aticonfig: No supported adapters detected
```I thought the shell script installed the driver? If not, how do I get it?

Much appreciated.

---

### Post by dlbueno on 2011-04-26
Did you ever get this to work? I'm considering the ASUS eee 1015t (the smaller screen version of the 1215t, I think) and I really would like to be able to watch videos in 720p.

---

