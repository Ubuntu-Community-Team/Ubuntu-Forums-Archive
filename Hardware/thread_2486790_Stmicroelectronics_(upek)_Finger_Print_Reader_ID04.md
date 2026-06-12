---
title: "Stmicroelectronics (upek) Finger Print Reader ID0483:2016"
date: 2023-05-10
forum: Hardware
---

### Post by aarcher77 on 2023-05-10
I have an old laptop with a fingerprint reader made by stmicroelectronics.  I have installed fprintd and libpam-fprintd and run pam-auth-update and I can enroll fingerprints just fine.  When an authentication prompt comes up, whether in the desktop session, at the cli, or at the login window, it asks me to swipe the finger enrolled as #0 (in my case, the most recent) but it will not respond to the swipe.  It doesn't say it failed, or error out; it just does nothing.  When I run fprintd-verify, it returns:
=====================================
[COLOR=#0000ff]Using device /net/reactivated/Fprint/Device/0[/COLOR]
[COLOR=#0000ff]Listing enrolled fingers:[/COLOR]
[COLOR=#0000ff] - #0: left-index-finger[/COLOR]
[COLOR=#0000ff] - #1: right-index-finger[/COLOR]
[COLOR=#0000ff]Verify started![/COLOR]
[COLOR=#0000ff]Verifying: left-index-finger[/COLOR]
[COLOR=#0000ff]Verify result: verify-disconnected (done)[/COLOR]
=====================================
  Does "disconnected" indicate a failure, or just the end of the process?

lsusb returns:
=====================================
[COLOR=#0000ff]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#0000ff]Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver[/COLOR]
[COLOR=#0000ff]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#0000ff]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#0000ff]Bus 003 Device 003: ID 0483:2016 STMicroelectronics Fingerprint Reader[/COLOR]
[COLOR=#0000ff]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#0000ff]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
===================================================

The strange thing is that it worked fine in Mint 19.3 but stops working after that version.  From what research I've done it's a driver issue beyond a certain version of Ubuntu.  If anyone knows of a fix, I'd really appreciate some help.  I have a soft spot for this old laptop and Linux Mint Tricia 19.3 has fallen out of support as of April so I've upgraded to Ubuntu Mate 22.04.

---

