---
title: "+ LiveCD (Intrepid Ibex) + CRT = problem"
date: 2008-12-23
forum: Hardware
---

### Post by CHaoSlayeR on 2008-12-23
Hi all,

I have a problem with the LiveCD for Kubuntu Intrepid Ibex. When I boot from the CD to try out the new version my monitors shut themself down to prevent damage. This is due to the fact that X is trying to initialize a 1600x1200 resolution with a horizontal frequency of somewhat aroung 120 kHz which is much above the 103 kHz the 19" CRT monitor is capable of (Iiyama Vision Master 450).

The LiveCD automatically chooses the radeon driver instead of the fglrx (which would be better with the HD2400 Pro). With the Hardy Heron LiveCD I didn't had such issues. It correctly set the initial resolution to 1280x1024@85Hz. The EDID information of the monitor correctly specifies the possible modes as it just specifies one 1600x1200 mode running at 60 Hz. So it can't be misleading monitor information.

Is there a way (some type of boot parameter or anything) that I can do to get the Intrepid LiveCD running on that machine **with** a graphical interface?

Thanx in advance,

C]-[aoZ

---

