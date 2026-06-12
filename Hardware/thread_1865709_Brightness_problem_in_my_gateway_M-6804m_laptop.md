---
title: "Brightness problem in my gateway M-6804m laptop"
date: 2011-10-20
forum: Hardware
---

### Post by 1544C on 2011-10-20
Hi all,
I am a new user to ubuntu(11.10), but I know how some things work.
Now I'm having a problem trying to adjust the brightness in my laptop:

```
cat /proc/cpuinfo | grep "model name" | tail -n 1
[COLOR=Red]model name    : Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz[/COLOR]
``````
lspci | grep VGA
[COLOR=Red]00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)[/COLOR]
```I have already tried adjusting the brightness in system settings, but the screen stays the same.

Could someone help me finding a solution to this?

---

