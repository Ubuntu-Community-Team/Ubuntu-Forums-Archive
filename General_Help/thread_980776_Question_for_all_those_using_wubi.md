---
title: "Question for all those using wubi"
date: 2008-11-13
forum: General Help
---

### Post by brandon88tube on 2008-11-13
This is a question for all of those using wubi, especially if you are using it on a laptop. I am trying to see if one of my problems is being causing by wubi or not.

Do any of you get the same results such as me for thermal readings using this command?```
$ acpi -V
     Battery 0: Full, 100%
  AC Adapter 0: on-line
     Thermal 0: ok, 0.0 degrees C
     Cooling 0: LCD 0 of 10
     Cooling 1: Processor 0 of 10
```
I seem to be getting 0.0 degrees C
Also I get this weird virtual output from lm-sensors and I wanted to know if wubi might be the cause of this. Here is the lm-sensors output.```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +0.0°C  (crit = +94.0°C)
```

---

### Post by brandon88tube on 2008-11-14
Really, can anyone using wubi tell me if they get 0.0 degrees C using the **acpi -t** command? Also if anyone has lm-sensors installed could you tell me if your output says virtual device using the **sensors** command?

---

### Post by ago on 2008-11-14
Is acpi active at all, cat /proc/cmdline

---

### Post by brandon88tube on 2008-11-14
This is the output ```
$ cat /proc/cmdline
root=UUID=1674B1EF74B1D1AB loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 

```

---

### Post by ago on 2008-11-14
That looks good, I would not think at this point that the issue is wubi related

---

### Post by brandon88tube on 2008-11-14
Thanks Ago, but now I'm left with no real options as to fixing my heat problem with Ubuntu. I tired in other sections of the forums with no luck. Guess I have to stop using Ubuntu now :(

---

### Post by GavinZac on 2008-11-14
> **brandon88tube said:**
> Thanks Ago, but now I'm left with no real options as to fixing my heat problem with Ubuntu. I tired in other sections of the forums with no luck. Guess I have to stop using Ubuntu now :(

Because you can't get an accurate heat reading? :/

---

### Post by brandon88tube on 2008-11-14
> **GavinZac said:**
> Because you can't get an accurate heat reading? :/

No, my laptop overheats really bad and I can't fix it. It runs fine in Windows so I know its not a hardware issue, but an issue with Ubuntu.

---

