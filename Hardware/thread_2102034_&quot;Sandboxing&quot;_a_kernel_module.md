---
title: "&quot;Sandboxing&quot; a kernel module?"
date: 2013-01-06
forum: Hardware
---

### Post by Ranko Kohime on 2013-01-06
Let's say we have a kernel module causing a hang.  (In my case, "iwlwifi" is causing a total and complete lockup, something that this particular module did 2 years ago the last time I tried it.)

Is there a way to sandbox a kernel module, such that it can be used, but if it faults, it could simply be killed as opposed to taking the entire system down with it?

---

