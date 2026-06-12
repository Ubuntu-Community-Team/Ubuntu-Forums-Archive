---
title: "Min. hardware for low-watt apache/tomcat/java solution"
date: 2009-08-19
forum: Hardware
---

### Post by mikeklein on 2009-08-19
Before I start spending some $$ I was hoping somebody with some experience in this area could recommend bare minimum cpu for handling a stack of say apache, tomcat, and of course j2se.

Cost if not as much a concern as watts/noise. I am looking for a platform which could handle say 1-5 users (reality is 1-2 for this scale) and not choke.

Rx-tx will also be running. Not that serio will be a problem.

I expect my tomcat app would have 10-30 app threads doing lightweight stuff like some polling, timers, etc.

Due to potential amount of logging and what's being logged disk speed shouldn't be too slow and capacities need to be large-ish...this should not be an issue on any hardware I think.

I think the amd geode is too puny....something like atom perhaps?Anything lower watt that can still run this stack decently?

Thanks in advance.

---

### Post by mikeklein on 2009-08-19
I decided on a dual-core Atom N330. Seems to be around 30-40w and apparently will do 1080p.

Total price with 2gb ram and 500gb 2.5 hdd is around $300.

---

