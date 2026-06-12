---
title: "Acer Aspire Laptop - BATTERY ISSUE"
date: 2011-07-25
forum: Hardware
---

### Post by spectrus_ on 2011-07-25
Recently my laptop has stopped recognizing my battery. I'd like to find out if my battery has died and needs replacement, or it's just not being recognized.

My laptop is an Acer Aspire 3810TZ. I'm running Ubuntu 11.04 Natty Narwhal. The battery worked fine for a long time, then all of a sudden, I shut it down and the next day it wouldn't start off battery power. It will only work while connected to a power supply.

I looked through various threads and sites looking for a solution and couldn't find one specific to my problem. I did, however, see someone mention "acpi", so I downloaded the package. The output when I type 'acpi' in terminal is as follows:

```

Battery 0: Unknown, 69%

```

If more information is needed, let me know. I appreciate your help.

EDIT:

acpi -V results:
```


Battery 0: Unknown, 69%
Battery 0: design capacity 5600 mAh, last full capacity 4730 mAh = 84%
Adapter 0: on-line
Thermal 0: ok, 26.8 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 127.0 degrees C
Cooling 0: LCD 0 of 9
Cooling 1: Processor 0 of 10

```

---

### Post by spectrus_ on 2011-07-26
Nothing...? Acer Customer support recommends I buy a new battery. I'd like to hear other people's input first.

---

### Post by ZaHACKieL on 2011-07-26
Hi there. Do you have dual boot in your laptop? If you do, have you tried the battery from Windows? Another option could be looking for the battery in the BIOS. Try that and let me know if you get anything.

---

### Post by spectrus_ on 2011-07-26
I do not have dual boot, therefore I can not try it on a different OS. I'll check on BIOS and edit in a moment or so (just fixing my conky config \\:D/).

---

