---
title: "i8k problems on Dell Inspiron 4100: keyboard lockup - fan miising proc file"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by transistor on 2006-11-15
I've loaded Dapper 6.06 onto a Dell Inspiron 4100. Picks up all the hardware. Excellent work everyone. Thank you very much.

I noticed the machine was running extremely hot and shutting down, found out about i8k and installed it. 

**Keyboard lock-up**
If I try
[INDENT]/sbin/modprobe i8k force=1[/INDENT]
and insert
[INDENT]i8k force=1[/INDENT]
into /etc/modules the keyboard locks up and doesn't recover on boot. This led to an interesting exercise on booting from the CD, mounting the hard drive and removing the line from /etc/modules. (This avoids re-installing Ubuntu on the hard drive.)

**i8kfan**
I've tried gkrellm and enabled the Dell i8k plugin but it reports 
[INDENT]gkrellm missing proc file err[/INDENT]
at which point the message appears to be truncated.

Any ideas?

Oops: Typo in the subject line. Should read "fan *missing* proc file"

---

### Post by transistor on 2006-11-21
I'm still overheating.
[http://www.math.ucla.edu/~jimc/insp4100/details.html](http://www.math.ucla.edu/~jimc/insp4100/details.html) reports that 
> The i8k.o module is included in recent kernels but the version in 2.4.16 (and before) does not recognize the Inspiron 4100. i8k v1.8 works on Inspiron 4100 without being force-loaded.
Synaptic reports i8kutils version 1.27 on my machine.

Can anyone suggest a procedure to resolve this?

---

### Post by n3rdism on 2006-11-23
my keyboard doesnt freeze up but when trying to run the i8k utilities i get "Can't open /proc/i8k: No such file or directory"

---

### Post by transistor on 2006-11-25
Sorry I don't know how to help you with that.

---

