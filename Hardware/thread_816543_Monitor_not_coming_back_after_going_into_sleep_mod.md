---
title: "Monitor not coming back after going into sleep mode."
date: 2008-06-02
forum: Hardware
---

### Post by ghstridr on 2008-06-02
I've got  a dell precision 690 with a nvidia Quadro FX 550 hooked up to two Dell 20"lcds via DV connections.
The driver version from nvidia being used (installed by Envy) is:
1:169.12+2.6.22-14

When the machine sits idle, the monitors go to sleep (as directed by the vid card). I hit a key on the keyboard or shake the mouse and only the #2 screen comes up. I have to hit ctrl-alt-bkspc to restart X and login again.
Really annoying.

Btw, the nvidia driver is set to use TwinView to stretch the one desktop across both monitors

Running Ubuntu 7.10
(Can't run 8 yet because vmware server won't compile and I need it)

---

### Post by gborzi on 2008-06-02
Have you tried the configuration suggested [here]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend")?

---

### Post by acron1 on 2008-06-02
Some computers have problems coming out of sleep.
You can try Ctrl+Alt+F1 followed by Ctrl+Alt+F7 and see if that restarts X.
Let us know how it goes.

---

### Post by ghstridr on 2008-06-04
> **acron1 said:**
> Some computers have problems coming out of sleep.
You can try Ctrl+Alt+F1 followed by Ctrl+Alt+F7 and see if that restarts X.
Let us know how it goes.

switching back and forth did wake up screen 0 and things came back, but I shouldn't have to do that every time.

---

