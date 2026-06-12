---
title: "ubuntu 16.04.4 desktop stuck on Dell Latitude 5580"
date: 2018-03-19
forum: Hardware
---

### Post by JavaPenguin on 2018-03-19
I installed Ubuntu 16.04.4 desktop on my Dell Latitude 5580.
After installation it asked to do a restart.
It is not shutting down.
It just keeps displaying this message on the terminal.

watchdog: BUG: soft lockup - CPU#2 stuck for 22s! [plymouth:28884]

If I try ubuntu before installing and run a lshw, it also hangs.

I have tried ubuntu 16.04.3, ubuntu mate 16.04.3, ubuntu 17.04, ubuntu mate 17.04 and linux mint 18.3.
Windows 10 install and shutdown successfully.

---

### Post by kerry_s on 2018-03-19
you mean it does that everytime, even after you hold the power button to force shutdown?

---

### Post by ivan-samuelson on 2018-03-19
This Linux Mint thread states the OP had an issue with his video card. He had to set the nomodeset setting to boot up which forces the GPU to display in software rendering mode. But then he could get the proper drivers installed after that. Might be an issue with your GPU not the CPU.

[https://forums.linuxmint.com/viewtopic.php?t=231558](https://forums.linuxmint.com/viewtopic.php?t=231558)

---

