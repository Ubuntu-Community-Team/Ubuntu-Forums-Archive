---
title: "Lenovo Yoga Battery life/calibration"
date: 2013-12-24
forum: Hardware
---

### Post by fissledizzle on 2013-12-24
I am running Ubuntu 13.10 on a Lenovo Yoga 11s. All common issues are solved (Brightness, Wireless, ...), but battery life is still a problem I could not find discussions for: 

The battery does not charge beyond 59% which results in a poor ~2 hours of battery life. (Also occured in 12.04 LTS)
Is there a battery calibration routine? What battery life do others achieve?

---

### Post by fissledizzle on 2013-12-28
I found the problem, however no sophisticated solution, yet.
Back in Win8 I changed the[ Lenovo Energy Managment Plan from 'Maximum Battery Runtime' to 'maximum Lifespan']("http://forums.lenovo.com/t5/Linux-Discussion/Z360-Ubuntu-Power-Management/m-p/310184#U310184"), which limits the upper battery charge state to 60%. Afaik There is no such option of choise in ubuntu. The only solution seems to be a tedious Win8 installation on USB. As for ThinkPads TLP can be used to set the charge thresholds, however the extended options of TLP for ThinkPads are not working witht the Yoga 11s.

[URL="http://forums.lenovo.com/t5/Linux-Discussion/Z360-Ubuntu-Power-Management/m-p/310184#U310184"]


[/URL]

---

