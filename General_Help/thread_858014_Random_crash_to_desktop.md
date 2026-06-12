---
title: "Random crash to desktop"
date: 2008-07-13
forum: General Help
---

### Post by neur0 on 2008-07-13
On average, approximately once every 5 days some application crashes very fast, but is still in the processes. I just get the desktop without any delay or error message. 
At first I thought it was the flash in Firefox but I see that this happens not only in Firefox.
Is there any way to diagnose it and know what has happened?

I'm running everything updated, and my average uptime is about a week.

---

### Post by billynomates on 2008-07-13
Could be a memory issue. What's your CPU usage like when a program crashes?

---

### Post by mempman on 2008-07-13
> **neur0 said:**
> On average, approximately once every 5 days some application crashes very fast, but is still in the processes. I just get the desktop without any delay or error message. 
At first I thought it was the flash in Firefox but I see that this happens not only in Firefox.
Is there any way to diagnose it and know what has happened?

I'm running everything updated, and my average uptime is about a week.

check your system logs at /var/logs.  You might want to check the syslog, and it is useful to check the log with a text editor or something that allows for you to use FIND function to limit your search down to a specific date and time.

---

