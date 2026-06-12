---
title: "Kubuntu Hangs on Shutdown (remote ssh still works)"
date: 2009-10-08
forum: Hardware
---

### Post by jbentham on 2009-10-08
It seems that one of the recent updates is causing my laptop and desktop to hang on shutdown (running 2.6.24-24-generic on both).

Here are the symptoms and what I have tried so far:
- the mouse is still active, but screen is black
- Ctl-Alt-Del does not work
- SSH from another computer works and I can execute a shutdown from there
- from an SSH session, /var/log/syslog shows the following at the end (it may or may not be related):
>>
Oct  8 11:00:45 alet-winlin-01 avahi-daemon[5727]: Invalid query packet.
Oct  8 11:00:46 alet-winlin-01 last message repeated 2 times
<<
- I have not made any hardware or software changes; only updates

I am not sure what else to look for in solving this.

Any ideas on what the problem is or how to fix it?

---

