---
title: "Upgraded to Heron, Boot time &gt; 3 min"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by Rayn on 2009-06-06
Just went up to Heron from Gutsy cause Gutsy was treating me fine but ...

I needed a new package.  So there I go, upgrade to Heron.  It now takes 3-4 minutes to start up.  Most of the time is spend staring at the Ubuntu logo watching the orange bit go back and forth.

How can I tell what is causing the issue?  I don't know where to look for such a thing.

Thank you.

---

### Post by markbuntu on 2009-06-08
You can look in System/Adminstration/System Log and look in the kern.log.0 or syslog. They are time stamped so you can see what is taking so long. You can use bum (boot up manager) to turn off services the kernel is trying to start that you don't need that are hanging up the boot process trying to get non-existent harware working.

Do you have all the updates?
If not run Update Manger.

---

### Post by Rayn on 2009-06-09
I am fully updated however

the logs you noted look just fine.

everything in kern.log and syslog start up in about 45 seconds

however the first entries there are a good 3 minutes after I issued my reboot command.

What is happening before entries to those files begin to be generated?  Anyway I can see that?

---

