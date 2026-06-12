---
title: "Missing /dev/ files"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by wachowim on 2005-04-21
Hi!

The problem is:
/dev/radio0 /dev/video0 used by my fm/tv card are missing. After one of dist-uprades before Hoary's final release, system during boot stopped loading bttv modules (which before that worked just fine) too.

When I load them manualy:
sudo modprobe bttv tuner
they load without a problem, but /devradio* and /dev/video* files are still missing.

Can someone help me write an udev rule file that would copy necessary files from /.dev/ ? :) Or maybe the problem lies somewhere else?

Thanks!

---

