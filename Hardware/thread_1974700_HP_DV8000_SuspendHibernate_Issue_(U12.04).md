---
title: "HP DV8000 Suspend/Hibernate Issue (U12.04)"
date: 2012-05-06
forum: Hardware
---

### Post by knotworking on 2012-05-06
Hello,
 
I've just installed the latest LTS release, 12.04, on my wife's HP DV8000 CTO laptop. I had to use a proprietary driver to get the WIFI working (that was actually tricky to find out, Ubuntu was not launching at install if I had the WIFI on, I was about to give up and decided to try disabling anything I could). Anyway, everything is working now EXCEPT the laptop will not Suspend or Hibernate. It goes into both modes fine, but it will not return, all the buttons light up, but the display stays blank. I've spent the last week reading about this issue, seems it's been a problem for years. It seems to be the ATI Radeon video card. I am about to uninstall the Radeon drivers and try the proprietary drivers to see if it fixes the issue, but I wanted to post here and see if anyone might have any suggestions before I head down this next rabbit hole.
 
The specifics:
- Ubuntu 12.04 64bit
- ATI Radeon Xpress 200m
- I am only using the sideport memory, not shared.
- 2gbs Ram (max allowed by the board)
 
Anyone seen a recent solution to this problem?

---

### Post by fnadde42 on 2012-05-12
I got the same problem mate. When I leave my computer it goes into sleep but when I try to wake it up nothing happens. Oh, and also when I press any button on the keyboard my mouse activates as long as I keep the button down.

---

