---
title: "speed inconsistencies"
date: 2006-03-21
forum: Hardware &amp; Laptops
---

### Post by Hacim on 2006-03-21
Hi everyone,I only had my ubuntu box up and runng for just under a week but so far its been great.Getting a dev inviroment set up was real simple and did not take to much getting use to since I was using mingw on winXp for a while anyway.But to get to my problem,I don't know if this is strictly a hardware issue or if some software plays a roll:the speed of the system goes up and down systematicly,like this    |   |   |    |
                             | | | | | | | | 
atleast thats how the system monitor applet shows it.When running higher performance apps it noticeble freezes for half a second and then runs fine for a little bit.Does any know what could cause this?Thanks.

by the way,here area the system specs:
celeron D 2.93 ghz 512mb ram 80gb hardrive MSI motherboard.

ok,thanks I used top and found that something was running perl scripts every little bit,so I started removing applets and when I romeved the modem-monitor applet the problem went a way (it also lockedup the task bar but its fine now).Thanks again:D

---

### Post by reet on 2006-03-21
Using a program like gnome-system-monitor or "top" (I like htop myself) will help you determine which process is using the CPU at those peaks.

---

