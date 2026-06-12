---
title: "Best way to debug/troubleshoot suspend/hibernate problems?"
date: 2009-10-02
forum: Hardware
---

### Post by cecilx22 on 2009-10-02
So, I am having issues with suspend/resume on my machine, and I am wondering if anyone out there can suggest a methodology to capture data while the system suspends, then while it attempts to resume to try and figure out whats going wrong.

Specifically, --sometimes-- the system resumes just fine, sometimes it stays at a black screen with the hdd access light blinking intermittently.

I am running a Dell Studio XPS16 laptop with a Radeon 4670 card.  I know this system -had- problems with suspend, but as of the last ATi driver, they were supposed to have been resolved.

Please let me know what logs to dump, etc.

Thanks in advance!!

-Ben

---

### Post by cecilx22 on 2009-10-14
Really?  nobody?

---

### Post by checkit on 2010-03-27
I realize this reply might be too late to be any use to you, but a good start would be to look at:
[LIST=1]
[*]dmesg
[*]/var/log/pm-suspend.log
[/LIST]
Also, have you looked at the following thread?

*Troubleshooting suspend and hibernate*
[http://ubuntuforums.org/showthread.php?t=1144999](http://ubuntuforums.org/showthread.php?t=1144999)

---

