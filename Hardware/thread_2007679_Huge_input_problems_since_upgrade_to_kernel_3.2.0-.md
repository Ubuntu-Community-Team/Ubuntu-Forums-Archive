---
title: "Huge input problems since upgrade to kernel 3.2.0-25-generic"
date: 2012-06-21
forum: Hardware
---

### Post by kosmos on 2012-06-21
Please note that while I know a lot about some areas of Linux/Unix, I'm a complete tyro with input devices.

My problem is that about once an hour since upgrading to kernel 3.2.0-25-generic, input becomes impossible, no sign of life from mouse or keyboard at all. I have to log in remotely to reboot.

This happened last night while I was playing a game under Wine.

My system is based on Ubuntu 12.04, but I do not use any desktop, I roll my own with the Sawfish window manager. I use Alsa instead of Pulseaudio. And I use Wine 1.2 as the games I use it for do not work in later versions.

Reverting to "3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64" fixes the problem.

Any hints on how I diagnose the problem, or what better information I could provide to help someone knowledgeable about input help me?

Thanks.

---

