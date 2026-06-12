---
title: "Can't install Ubuntu Trusty black screen. GTX 750 Ti"
date: 2014-05-19
forum: Hardware
---

### Post by cat-casho on 2014-05-19
I'm having trouble installing Ubuntu 14.04 from usb stick. I can see the options for trying, installing, check disk for errors but if choose any of them it's just a black screen. I can hear a jingle when I try "Try before installing" and "installing ubuntu" options but all I see is a black screen.
I have Intel i5 4570, GTX 750 Ti with 4GB of RAM.

---

### Post by norbert23 on 2014-05-20
Just a generic tip:
Please try to change to text-mode with ctrl+alt+f1 or ctrl+alt+f2 when you think the test-system loaded.
Can you do that? If yes - you could try to see the output in /var/log/Xorg.0.log

Maybe this helps (also try searching the web yourself):
[http://askubuntu.com/questions/425140/unable-toboot-with-nvidia-gtx-750-ti-even-with-latest-beta-drivers](http://askubuntu.com/questions/425140/unable-toboot-with-nvidia-gtx-750-ti-even-with-latest-beta-drivers)

---

### Post by cat-casho on 2014-05-21
[COLOR=#333333][FONT=Tahoma]I fixed the problem. I have to unplug my Graphics card and use the graphics chip built into my CPU to get past the install process then I have to manually install the latest Nvidia drivers since the open source Nouveau drivers don't support my GPU yet.[/FONT][/COLOR]

---

