---
title: "Suspend on Lid closing doesn't work"
date: 2008-05-28
forum: Hardware
---

### Post by mojo17 on 2008-05-28
Hello,

I've been using Kubuntu for about 2 yrs on my Dell Inspiron 5100 laptop, and I have an interesting problem that I was unable to solve yet. Closing the lid does not cause the laptop to suspend despite the fact that I have chosen this action in the Power Manager applet. Suspending from the Logout/Shutdown screen works perfectly. What's interesting is that if I suspend manually, close the lid,  then open the lid again, the system will wake up normally.
I can confirm that the issue is not related to hardware malfunction because my other windows partition does not have this issue with lid actions.
Also, I created a small bash script to read /proc/acpi/button/lid/LID/state every second, and I am able to confirm that the state changes from 'open' to 'closed' when the lid is closed.  For some reason, the system is responding properly to Lid Open events, but not to Lid Closed.

I suspect that Power Manager isn't properly saving my settings. 
Where should I be checking next?

Thanks

---

### Post by Cclips on 2008-07-12
Are you running any programs? I found my 1420 wouldn't suspend if I was still running rythem Box for example, but would if I closed it (the prgram, not the lid).

---

