---
title: "Laptop gets very hot in a few minutes after boot up"
date: 2011-05-21
forum: Hardware
---

### Post by sridarshan on 2011-05-21
I'm using lenovo R61,dual booted with window 7 and ubuntu 10.04 . Dual booting since 2 years, no problem since then. But from a past few days,Ive been noticing that, in Ubuntu, My laptop becomes unbearably hot .Should I be worried?

---

### Post by rvchari on 2011-05-21
> **sridarshan said:**
> I'm using lenovo R61,dual booted with window 7 and ubuntu 10.04 . Dual booting since 2 years, no problem since then. But from a past few days,Ive been noticing that, in Ubuntu, My laptop becomes unbearably hot .Should I be worried?

could be a cause as some of your processes must be consuming lots of resources. in my case it is gnome appearance. whenever i choose to change the appearance properties by right clicking on the desktop, the temp shoots up from its usual 40 + to 60 + in just a few seconds. for this, i run conky which shows the top processes with its process id (pid). 

i notices that there was a 2nd instance of the process gnome appearance running paralleley with the first one. when i killed that process (2nd one that shows up on top of list) temp came down to its normal.

to study this, run "top" command without the quotes in terminal. this should tell you which are the killer apps thats eating ur laptop. try to kill them by issuing a command "kill PID no" without the quotes and see the difference.

i am facing this since past few months and since then i run conky to display the temp and top processes.... essentially to keep track of whats happening !

hope this suggestion will help you track your problem process that may be running parallelly in multi modes thats eating your resources. also check the start up apps and minimize them if possible.

---

