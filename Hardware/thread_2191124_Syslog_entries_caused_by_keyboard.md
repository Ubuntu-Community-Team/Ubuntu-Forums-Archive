---
title: "Syslog entries caused by keyboard"
date: 2013-12-01
forum: Hardware
---

### Post by m-eberlein on 2013-12-01
Hello,

just running a dual-boot system with Win7 prof and Ubuntu 12.04LTS on a separate HDD. My Ubuntu is not stable at all.
Running a Radeon graphics-card, don't know, if this matter. Now, I recognized some strange behaviour...
every keypress of my keyboard results in an entry in the syslog. Same with my mouse...

```
tail -f /var/log/syslog
```

will result in this...

```
Dec  1 09:37:33 linuxtower kernel: [ 2426.279512] evbug: Event. Dev: input2, Type: 4, Code: 4, Value: 29
Dec  1 09:37:33 linuxtower kernel: [ 2426.279519] evbug: Event. Dev: input2, Type: 1, Code: 29, Value: 2
Dec  1 09:37:33 linuxtower kernel: [ 2426.279523] evbug: Event. Dev: input2, Type: 0, Code: 0, Value: 0
Dec  1 09:37:33 linuxtower kernel: [ 2426.312717] evbug: Event. Dev: input2, Type: 4, Code: 4, Value: 29
Dec  1 09:37:33 linuxtower kernel: [ 2426.312725] evbug: Event. Dev: input2, Type: 1, Code: 29, Value: 2
Dec  1 09:37:33 linuxtower kernel: [ 2426.312729] evbug: Event. Dev: input2, Type: 0, Code: 0, Value: 0
Dec  1 09:37:33 linuxtower kernel: [ 2426.345918] evbug: Event. Dev: input2, Type: 4, Code: 4, Value: 29
Dec  1 09:37:33 linuxtower kernel: [ 2426.345925] evbug: Event. Dev: input2, Type: 1, Code: 29, Value: 2
Dec  1 09:37:33 linuxtower kernel: [ 2426.345929] evbug: Event. Dev: input2, Type: 0, Code: 0, Value: 0
Dec  1 09:37:33 linuxtower kernel: [ 2426.379119] evbug: Event. Dev: input2, Type: 4, Code: 4, Value: 29
Dec  1 09:37:33 linuxtower kernel: [ 2426.379126] evbug: Event. Dev: input2, Type: 1, Code: 29, Value: 2
Dec  1 09:37:33 linuxtower kernel: [ 2426.379131] evbug: Event. Dev: input2, Type: 0, Code: 0, Value: 0
Dec  1 09:37:33 linuxtower kernel: [ 2426.412323] evbug: Event. Dev: input2, Type: 4, Code: 4, Value: 29
Dec  1 09:37:33 linuxtower kernel: [ 2426.412331] evbug: Event. Dev: input2, Type: 1, Code: 29, Value: 2
Dec  1 09:37:33 linuxtower kernel: [ 2426.412335] evbug: Event. Dev: input2, Type: 0, Code: 0, Value: 0
Dec  1 09:37:33 linuxtower kernel: [ 2426.445528] evbug: Event. Dev: input2, Type: 4, Code: 4, Value: 29
Dec  1 09:37:33 linuxtower kernel: [ 2426.445535] evbug: Event. Dev: input2, Type: 1, Code: 29, Value: 2
Dec  1 09:37:33 linuxtower kernel: [ 2426.445539] evbug: Event. Dev: input2, Type: 0, Code: 0, Value: 0
Dec  1 09:37:33 linuxtower kernel: [ 2426.478725] evbug: Event. Dev: input2, Type: 4, Code: 4, Value: 29
Dec  1 09:37:33 linuxtower kernel: [ 2426.478732] evbug: Event. Dev: input2, Type: 1, Code: 29, Value: 2
Dec  1 09:37:33 linuxtower kernel: [ 2426.478736] evbug: Event. Dev: input2, Type: 0, Code: 0, Value: 0
Dec  1 09:37:33 linuxtower kernel: [ 2426.511928] evbug: Event. Dev: input2, Type: 4, Code: 4, Value: 29
Dec  1 09:37:33 linuxtower kernel: [ 2426.511935] evbug: Event. Dev: input2, Type: 1, Code: 29, Value: 2
Dec  1 09:37:33 linuxtower kernel: [ 2426.511940] evbug: Event. Dev: input2, Type: 0, Code: 0, Value: 0
Dec  1 09:37:33 linuxtower kernel: [ 2426.550059] evbug: Event. Dev: input2, Type: 4, Code: 4, Value: 29
Dec  1 09:37:33 linuxtower kernel: [ 2426.550066] evbug: Event. Dev: input2, Type: 1, Code: 29, Value: 0
Dec  1 09:37:33 linuxtower kernel: [ 2426.550070] evbug: Event. Dev: input2, Type: 0, Code: 0, Value: 0
Dec  1 09:37:34 linuxtower kernel: [ 2427.505187] evbug: Event. Dev: input2, Type: 4, Code: 4, Value: 29
Dec  1 09:37:34 linuxtower kernel: [ 2427.505194] evbug: Event. Dev: input2, Type: 1, Code: 29, Value: 1
Dec  1 09:37:34 linuxtower kernel: [ 2427.505198] evbug: Event. Dev: input2, Type: 0, Code: 0, Value: 0


```

could this be the reason my system is so buggy?

---

### Post by m-eberlein on 2013-12-04
Please close this thread. Will post on another forum. thanks.

---

