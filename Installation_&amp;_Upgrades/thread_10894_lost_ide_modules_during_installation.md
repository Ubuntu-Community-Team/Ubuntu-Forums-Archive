---
title: "lost ide modules during installation"
date: 2005-01-12
forum: Installation &amp; Upgrades
---

### Post by Rodin on 2005-01-12
Hi everyone!
I'recently bought an used Dell Cpi Latitude D266XT and upgraded it with a PII 400 Mhz.It works fine with a Slack 10.0,but  I want to install Ubuntu on it(I already use it on my home LAN).I'm going mad with an installation problem on this laptop.During the modules loading (at first cd boot),I can see on tty4 debug console that hw-detect can't find the following ones:
ide-mod
ide-probe-mod
ide-detect
ide-floppy
Subsequently a "syslog.info klogd: ide-cd "cmd 0x28 timed out" " error causes an infinite loop trying to recover the DMA interrupt for /dev/hdc forcing me to phisically shut down the laptop.
I also tried "linux nodma noscsi" at boot prompt but with no results.
Again I tried to manually load the modules as described in:

[https://bugzilla.ubuntu.com/show.bug.cgi?id=1440](https://bugzilla.ubuntu.com/show.bug.cgi?id=1440)  comment #42 and #43 but I'm not able to find them.

Hints appreciated.TIA
P.S.:Excuse me for my bad English!

Lorenzo
Italy

---

