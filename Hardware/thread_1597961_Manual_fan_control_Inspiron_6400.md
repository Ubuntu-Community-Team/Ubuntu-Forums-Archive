---
title: "Manual fan control Inspiron 6400"
date: 2010-10-15
forum: Hardware
---

### Post by dumb_question on 2010-10-15
I have an Inspiron 6400 which has overheating problems (the display gets flaky when the machine gets hot). I just realized I can't remember the last time I heard the fan go on, and I am wondering if it's dead, or maybe a software issue. Is there a straightforward way to turn on the fan from the command line so I can see if it's working (and maybe solve my heating issues that way)?

Currently using Maverick, /proc/acpi/fan/ is completely empty, and pwmconfig gives:

"/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed"

any thoughts?

---

### Post by dave2001 on 2011-02-19
just upgraded to 10.04 and I have the same problem with lack of fan activity. I'm on a thinkpad a20m. I think the problem is ACPI can't see my fan. My previous version of ubuntu(8.04), I was using apm instead of acpi and things worked much better. Haven't found a solutions yet for 10.04.

---

### Post by dumb_question on 2011-02-19
I am not on that machine right now but I finally solved the problem using gkrellm ([https://secure.wikimedia.org/wikipedia/en/wiki/GKrellM](https://secure.wikimedia.org/wikipedia/en/wiki/GKrellM))

---

