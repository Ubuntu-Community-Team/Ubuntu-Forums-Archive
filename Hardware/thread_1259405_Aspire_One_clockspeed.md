---
title: "Aspire One clockspeed"
date: 2009-09-06
forum: Hardware
---

### Post by blazemore on 2009-09-06
I have an Aspire One A100 (or something)
It has an Atom processor, which apparently runs at 1.6 GHz

Now take a look at this:
```
becky@becky-aspire-one:~$ cat /proc/cpuinfo 
processor	: 0
...
model		: 28
model name	: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
...
cpu MHz		: 800.000
...

And again (dual core CPU I guess)

```

Why does this say 800 mHz?

---

### Post by Fafler on 2009-09-06
You probably have speedstepping enabled. Try making some fake load with

```
dd if=/dev/urandom of=/dev/null
```and cat again.

---

