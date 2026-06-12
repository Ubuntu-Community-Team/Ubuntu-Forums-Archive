---
title: "monitor power management"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by nixIT on 2009-05-22
Hello all,

Recently installed 9.04, things went smoothly and so far Ubuntu hasn't let me down.

Under Screen Saver/Power management I have the setting "Put Display to sleep after inactive for 15 minutes".

However, my monitor never truly goes to sleep, the screen just dims, and the power light on my monitor is still Green, the monitor never goes off and the power light never turns amber.

This worked in 8.10.

Any ideas how to get the power management to turn off the display after inactive?

--nixIT

---

### Post by nixIT on 2009-05-24
anyone else having this issue?

---

### Post by hilltop on 2009-06-06
Am having the same issue.  Running a Dell 2408WFP and restricted nvidia driver 180.44 from the repository.  Not good because this big monitor draws a lot of power for an LCD.  I thought about making some changes in the Configuration editor but have not done so yet.  This is an annoyance.

---

### Post by zubin71 on 2009-06-06
$ xset dpms 0 0 120

the above command sets your monitor to turn off after 120 seconds. hope that helps. 
Also, im working on an open source project named powerX which aims to improve power management in ubuntu 9.04
check out the details at :-

[http://www.p0werx.wordpress.com](http://www.p0werx.wordpress.com)

hope all of this helps!!!

---

### Post by nixIT on 2009-06-10
> **hilltop said:**
> Am having the same issue.  Running a Dell 2408WFP and restricted nvidia driver 180.44 from the repository.  Not good because this big monitor draws a lot of power for an LCD.  I thought about making some changes in the Configuration editor but have not done so yet.  This is an annoyance.

check out my post here.  I figured it out.

[http://ubuntuforums.org/showthread.php?t=1169794]("http://ubuntuforums.org/showthread.php?t=1169794")

---

