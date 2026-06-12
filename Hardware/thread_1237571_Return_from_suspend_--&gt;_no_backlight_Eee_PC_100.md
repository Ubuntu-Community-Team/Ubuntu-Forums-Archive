---
title: "Return from suspend --&gt; no backlight Eee PC 1000HEB"
date: 2009-08-11
forum: Hardware
---

### Post by Chronon on 2009-08-11
I think I am seeing a regression in version 2.6.28-14 of the kernel.  I find that when I suspend and try to wake my netbook it does so but without any backlight.  I can faintly see the screen in proper lighting and have been able to log out.  Doing so brings up a back lit login screen but the backlight again fails as soon as I successfully log in.  

I have had this happen consistently lately, though I'm not certain that I noticed this immediately after a kernel upgrade.  My reason for suspecting a regression is that booting the 2.6.28-13 kernel does not exhibit this problem.  Any other users experiencing this?  I would like to confirm that others experience this and figure out what set of factors reliably causes this condition before filing a bug report.

I found a bug report already filed and added a comment.  

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357073](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357073)

---

