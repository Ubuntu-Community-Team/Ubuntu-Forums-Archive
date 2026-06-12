---
title: "Can't track down why laptop won't suspend / hibernate  in 10.04"
date: 2010-07-12
forum: Hardware
---

### Post by vysotsky on 2010-07-12
Since upgrading to 10.04 LTS 64-bit, my HP Pavilion dv4t-1000 laptop has hung when I try to suspend the system: everything seems to go well at first, the screen blinks off for a moment, then suddenly the backlight turns back on with a blank screen and the computer hangs and is totally unresponsive.

I've looked through the system logs, but I'm having trouble tracking down the problem. I've looked at the syslog and the pm-suspend log, and neither of them seem to show any problem. (I'm seeing lots of messages that end with "success" before "performing suspend" and then nothing until the point where I restarted the machine.) 

Can anyone tell me how to proceed? What should I look for that might cause the problem?

I've had no problem suspending and hibernating on previous versions of Ubuntu, so I'm hoping this won't be too complicated to fix once I figure out what's going wrong. I'd be happy to attach logfiles if anyone can tell me which ones might be relevant for diagnosing the problem.

---

### Post by pboerr on 2010-07-14
I have exactly the same symptoms, and after several minutes looking for a workaround, i temporarily surrender :S

---

