---
title: "Automatic Wakeup after Suspend"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by librano on 2006-06-20
Hi all!

I am using an Acer Aspire 3003NLMi laptop which seems to be working pretty well with Ubuntu. I used to Mandriva 2006 till 6.06 was realeased and I'm glad to say that the power control is much better with Ubuntu... I am able to Hibernate, Suspend and resume without problems...

One thing I havent figured out though... I use my laptop as my alarm in the morning blasting my favorite tunes using xmms-alarm plugin... nothing else is loud enough to wake me up :lol: ... but i would like to suspend my laptop when i sleep and then automatically get it to wake up at a set time so that xmms-alarm can start the playlist... is there a way to do this? I would prefer this than just turning off the backlight of the screen...

Thanks in advance and thanks for a great distro... Ubuntu rocks!

lib.

---

### Post by ranf on 2006-06-20
This file looks like it could be used for this purpose:
```
cat /proc/acpi/alarm
```

[http://acpi.sourceforge.net/documentation/alarm.html](http://acpi.sourceforge.net/documentation/alarm.html)

---

