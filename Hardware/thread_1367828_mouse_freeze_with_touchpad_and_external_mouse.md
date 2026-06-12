---
title: "mouse freeze with touchpad and external mouse"
date: 2009-12-29
forum: Hardware
---

### Post by yesmelord on 2009-12-29
Hi,

I installed Ubuntu (Karmic Koala) on my Compaq Presario V5000 laptop. Everything except the Mouse works fine. I even got the wireless working. The mouse freezes quite often. The symptoms are that at seemingly random times, all of the buttons stop working on the mouse, usually when I am using firefox. When this happens, the system will respond to keystrokes. This happens with both the touchpad mouse and an external mouse. The CPU doesn't seem to be spiking. The mouse button will work again after a while if I just keep clicking the left and right buttons over and over again. Sometimes it wont come back and I have to reboot. This has gotten so annoying that I am ready to install another OS. Can anyone point me to a thread for this issue, or is there a fix? I've searched and it seems others have the same problem, but I haven't seen any solutions.

Thanks

---

### Post by NNing on 2010-02-11
i have the same problem.

advice so far includes:

- add a specific command line (see first link below)
- update Bios
- add to boot line (from older advice)
- replace Karmic with earlier version (but some of these had same bugs)
- roll back to an earlier version of Firefox 
- hope that Ubuntu finds a fix to this bug

please could you update this thread if you have any further info on this.



FYI, I have Nvidia graphics on Asus motherboard with Intel chip. It's a desktop so no touchpad issue but if I plug in another mouse while the other one is frozen, within seconds it gets the same problem. I'm also fairly new to Ubuntu, using 9.10, and the mouse now freezes randomly but the keyboard (and everything else) is ok. I have to ctrl-alt-del to reboot or shut down.



**Links:**

[http://ubuntuforums.org/showthread.php?t=1308931&highlight=mouse+freeze](http://ubuntuforums.org/showthread.php?t=1308931&highlight=mouse+freeze) (suggests adding a command line. I'm hoping this will work. See post by Musarraf172)

[http://www.uluga.ubuntuforums.org/showthread.php?p=8267830](http://www.uluga.ubuntuforums.org/showthread.php?p=8267830) (suggests updating Bios. That's also been suggested elsewhere.)

[http://www.fix-desktop-problems.com/desktop-hardware-problems/my-mouse-hangsfreezes-in-ubuntu-9-10](http://www.fix-desktop-problems.com/desktop-hardware-problems/my-mouse-hangsfreezes-in-ubuntu-9-10) (bug)

[https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/113344](https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/113344) (also bug)

[http://forums.techarena.in/operating-systems/1283431.htm](http://forums.techarena.in/operating-systems/1283431.htm) (re update drivers or roll back Firefox)

[http://www.linuxquestions.org/questions/linux-hardware-18/mouse-pointer-is-freezing-567964/](http://www.linuxquestions.org/questions/linux-hardware-18/mouse-pointer-is-freezing-567964/) (old reply - 2007)

[http://ubuntuforums.org/showpost.php?p=3003669&postcount=32](http://ubuntuforums.org/showpost.php?p=3003669&postcount=32) (add to boot line - old - 2007)

[http://ubuntuforums.org/showthread.php?t=976714](http://ubuntuforums.org/showthread.php?t=976714) (mouse freeze with 8.10 but also with NVIDIA graphics card)

[http://ubuntuforums.org/showthread.php?t=1396204&highlight=mouse+freeze](http://ubuntuforums.org/showthread.php?t=1396204&highlight=mouse+freeze) (seemingly unresolved but marked as solved)

[http://ubuntuforums.org/showthread.php?t=1324273&highlight=mouse+freeze](http://ubuntuforums.org/showthread.php?t=1324273&highlight=mouse+freeze) (another unresolved post marked as solved. I've added my 2 bobs' worth there too.)

[http://ubuntuforums.org/showthread.php?t=1324273&highlight=mouse+freeze](http://ubuntuforums.org/showthread.php?t=1324273&highlight=mouse+freeze) (another unresolved post that I've added to.)



After I try 1 or 2 of above, will update thread for anyone else with the problem. (looks like there are a few.)

Cheers,
NiNo.

---

### Post by NNing on 2010-02-11
freezing of different things in 9.10 seems to be a known bug that 'they' are working on.... do you have NVIDIA and/or Intel amongst your hardware? it came up in this thread:

[http://ohioloco.ubuntuforums.org/showthread.php?t=1309015&page=15](http://ohioloco.ubuntuforums.org/showthread.php?t=1309015&page=15)

suggestions (p.15) include rolling back to previous kernel. 

if you're a beginner like me, this sounds like it will be fun, right?

anyway, it's another thing to try.


btw, mention of the kernel problem is also here: 

[http://forums.techarena.in/operating-systems/1269693.htm](http://forums.techarena.in/operating-systems/1269693.htm)


cheers,
NiNo.

---

