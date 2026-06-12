---
title: "Compaq Armada M300 Battery ACPI/Hotkey Problem"
date: 2005-10-06
forum: Hardware &amp; Laptops
---

### Post by zzazaz on 2005-10-06
Hi! I'm running Ubuntu breezy on a Compaq Armada M300 and running into
2 problems.

1. ACPI Battery Info is invalid. How can I fix it?

I've purchased a large capacity 4.4 Ah replacement battery, but ACPI
is only showing 1.6 Ah.

$ less /proc/acpi/battery/C123/info
present:                yes
design capacity:        24000 mWh
last full capacity:     24000 mWh
battery technology:     rechargeable
design voltage:         14400 mV
...
battery type:           LIon
OEM info:               COMPAQ

ACPI claims I can only run on battery for 1:45 min, but I can run the
laptop on battery around 3-4 hours. Is there any way to fix the ACPI
info to get a more acurate battery run time?

2. Keyboard hotkey..

On the M300 there are several media keys that's not recognized by
Ubuntu. The power button, info, home, search, and mail button, which
sits right above the keyboard does not work in linux. Either power
button on the side or above keyboard boots the computer, but once in
linux, only the side power switch will initiate shutdown, the top
button no longer functions.

I've looked into using hotkeys to assign functions to the button, but
I don't get a key code whether using xev or showkey -s. I really don't
care about the multimedia keys, but I would like to assign the top
button for hibernate functions. Any suggestions???

Thanks!

EDIT:

ok, I got a little further on the keyboard issue, the multimedia key generates error into /var/log/kern.log regarding key not bound, so I was able to assign it based on input.h file. Once the keys are assigned, I can work with hotkeys to get them programmed. The power button above keyboard, no luck, it does not spew any errors. I've looked at an article regarding hacking acpi functions. I'll admit I don't completely understand it, though I found out ACPI use IRQ 9 on the m300. The article said if I cat /proc/acpi/events, I should be able to see the interrupt, and I was hoping to see it capture the key (lidclose, power, etc). Unfortunately the file is in use so I can't read it. Anyhow, I'll organize this a bit better and post some details next time.

---

### Post by daller on 2005-12-07
IMO this is the greatest howto concerning multimedia-keys:
 
 [http://ubuntuforums.org/showthread.php?t=27039](http://ubuntuforums.org/showthread.php?t=27039)

---

