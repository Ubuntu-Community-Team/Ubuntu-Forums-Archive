---
title: "Weird hanging problem, can't even type ps"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by synic on 2005-04-19
Hello,

I'm running 2.6.10-686-5 on an AMD XP 2400+.  I have a weird problem that has happened twice now - unfortunately I don't have a lot of information about it.  I tried launching firefox, but nothing came up - so I brought up a terminal and tried to type ps fax to see if there was a stagnant process running.  ps fax just hung.

So, I try to reboot.  Reboot hangs.  I have to power off the machine, and power it back on.

Any ideas?

Adam

---

### Post by AndersAA on 2005-04-19
when it happens try dmesg

or strace ps aux

(install strace first, so you have it when you need it ;) ).

---

### Post by synic on 2005-04-19
Hrmm, not quite sure why this post showed up in KDE.

I'll try your suggestion.  Thanks.

---

### Post by synic on 2005-04-19
Ok, the same exact thing just happened on my work machine, so I know it's not just machine specific now.

I did manage to catch an strace of ps fax. The log can be seen here: [http://linuxhelp.homeunix.com/strace.txt](http://linuxhelp.homeunix.com/strace.txt).  Note that this is not the only command that I can't run.  I can't run aplay, several other commands.

Could someone move this post into hardware?

Adam

---

### Post by AndersAA on 2005-04-19
gonna guess this is a kernel error, which is why we need dmesg output, it hangs on a read from /proc.

I've had this bug once too, but I haven't been able to reproduce it, and I didn't grab dmesg output when it happened.

---

### Post by synic on 2005-04-19
Oh, right, sorry.  

There is no helpful information in dmesg.  Just normal boot messages.

dataw0lf suggested it might be a conflict between aplay and esd.  I've disabled esd, will let you know if this fixes the problem.

Adam

---

### Post by AndersAA on 2005-04-19
hm... another thing that might be worth a try is after the strace.  Check the last line, for example:
open("/proc/21364/cmdline", O_RDONLY)   = 6

and do fuser -vm "/proc/21364/cmdline"

---

