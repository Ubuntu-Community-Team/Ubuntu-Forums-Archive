---
title: "What happened to hardware support with edgy?"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by Max Luebbe on 2006-11-03
Don't get me wrong - there are a lot of things I like I about edgy eft. I've been an Ubuntu user since 4.10, and have no intention of jumping ship anytime soon. 

Hardware support seems to have really taken a step in the wrong direction on this release though - my power management no longer works, my lcd brightness can no longer be adjusted, my wireless card no longer can scan for networks in the administration tool, and my nvidia graphics card no longer gets any type of decent performance without binary drivers.

Looking around the forums it seems that there are plenty of similar stories. Anybody else noticed this? Any suggestions on what we can do as a community to make sure 7.04 is as rock solid as Dapper was?

---

### Post by Jussi Kukkonen on 2006-11-03
The good news (in some sense) is that we don't have to wait for 7.04 -- regressions from previous versions can be fixed with updates. That's the guideline at least.

Often regressions aren't regressions though: I was certain my ethernet adapter driver had a serious bug in the Edgy version. It turned out that new kernels have a feature that turns off all usb devices that ask for more current than can be provided, and my ethernet adapter did that...

---

