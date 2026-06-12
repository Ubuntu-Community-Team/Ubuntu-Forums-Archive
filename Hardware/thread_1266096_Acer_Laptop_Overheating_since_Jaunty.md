---
title: "Acer Laptop Overheating since Jaunty"
date: 2009-09-14
forum: Hardware
---

### Post by Prosis on 2009-09-14
Hello

I've been on Jaunty for a couple of months but my new Acer 5535 becomes very hot.  It didn't do that on Intrepid nor on Fedora only Jaunty.

So much so it randomly shuts down which is very very annoying.

I searched here and google but I can't get any solution to work (of course I don't understand them all).

Example:

```
root@dl:~# modprobe powernow-k7
FATAL: Module powernow_k7 not found.
root@dl:~# modprobe cpufreq_conservative
FATAL: Module cpufreq_conservative not found.
root@dl:~# modprobe cpufreq_ondemand
FATAL: Module cpufreq_ondemand not found.
root@dl:~# modprobe cpufreq_powersave
FATAL: Module cpufreq_powersave not found.
root@dl:~# modprobe cpufreq_stats
FATAL: Module cpufreq_stats not found.
root@dl:~# modprobe cpufreq_userspace
FATAL: Module cpufreq_userspace not found.
```

Help? :)

---

### Post by earthpigg on 2009-09-14
is anything uselessly eating up CPU cycles?

```
top
```

i have heard mention that 'remote desktop viewer' has done this for some folks in jaunty.

it can be disabled in system -> preferences -> startup applications

---

### Post by Prosis on 2009-09-14
Not to my knowledge.  And Remote Desktop isn't in the startup list.

Things is when I work I need to work with a VM running Ubuntu Jaunty Server.  So that takes up a lot.

But I tried Linux Mint last week end and it did the same thing (without a VM running)

---

