---
title: "External Monitor on hp dm3z resets to mirrored image"
date: 2011-11-21
forum: Hardware
---

### Post by gatzby on 2011-11-21
In ubuntu 10.10, I could not use my hdmi port (it kept 'flashing' every few minutes or so).  This was fine, because my VGA port worked rather well, and all is dandy.

After upgrading to 11.04, the hdmi port works better, but upon resuming from sleep, the laptop hangs.

Additionally, in both VGA and HDMI output modes, at seemingly random times, the computer decides that I don't actually want to have an external monitor with extended desktop, and resets to mirrored display at 800x600 resolution (really annoying).

I don't even know what to search for to fix this issue, and trying to find these issues in dmesg is extremely frustrating as the timestamps don't actually contain a human readable time (/rant).

This happens in 11.10 too, and in short upgrading to that is a non-solution anyway, for reasons that have to do with the desktop environments.

I have a radeon card in the laptop, with lspci reporting this:

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]

Has anyone seen this type of issue before, or know how to fix it? I can provide whatever logs will help diagnose this.

Thanks in advance!

---

