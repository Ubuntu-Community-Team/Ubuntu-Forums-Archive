---
title: "How Do I Diagnose Suspend/Hibernate Failures?"
date: 2008-08-02
forum: General Help
---

### Post by Windsurfer619 on 2008-08-02
Hi
I own a Dell 640m laptop (it's sort of old) and I get a hard crash about 1 in every 3 or 4 suspends/hibernates. I was wondering how I could figure out what's causing these boot-up failures.
Basically, CTRL+ALT+backspace does nothing, and neither does REISUB, so it's something major, I'm assuming.
Thanks!

---

### Post by pytheas22 on 2008-08-02
Your system logs would be the first place to look.  You can view logs in a nice GUI by going to System>Administration>System Log, or you can find them all in the /var/log directory of your system.  Look especially at syslog and kern.log, and find out which messages were dumped to the log around the time that you tried to suspend or hibernate the system.  If you see anything interesting, google for the message or post it here.

It can also be useful when trying to solve suspend/hibernation issues to google your motherboard name + ubuntu/linux + suspend/hibernate...usually it comes down to having to tweak something related to your motherboard (although video and networking drivers also tend to have issues with suspend and hibernate).

---

