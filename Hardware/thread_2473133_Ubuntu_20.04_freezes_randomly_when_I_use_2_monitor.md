---
title: "Ubuntu 20.04 freezes randomly when I use 2 monitors (Dell, Iiyama)"
date: 2022-03-25
forum: Hardware
---

### Post by sandroe on 2022-03-25
Hello, everybody. I am a newbie in Linux. Hope, you help me.
I have fresh installed ubuntu 20.04 on my PC. I also installed 470 tested nvidia driver for my 1050 GPU. 1 or 2 times in a day my system absolutely freezes (no mouse or keyboard action). Only hard reset works (but i didn't try to connect via ssh).
I modified file etc/systemd/journald.conf with:
Storage=persistent
But when I viewed log with "journalctl -b - 1" after reboot there were no typical errors before freezing.

I use one monitor now and there is no freezes for two days
My xorg files in attachments (I could not see any errors here too)

How can I find the certain problem and fix it? thnx

---

