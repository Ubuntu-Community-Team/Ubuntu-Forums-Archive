---
title: "[SOLVED] Lower power consumption"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by ChrisMP1 on 2008-01-21
My computer has always had problems with suspend (even on Windows), and Ubuntu hibernate just doesn't cut it. I don't want to leave my computer on all the time, but I can't wait for it to boot when I need it. Is there some way from the command line to shut down certain parts of the computer to lower its power consumption? Any way to turn various parts off (echo foo > /sys/bar, etc.)?

---

### Post by tgalati4 on 2008-01-21
What is your hardware?  Suspend can be made to work.  I use SLED10 on an old Dell PIII machine and it suspends fine--power drops from~90 watts to 33 watts.  5 seconds to suspend-to-RAM, 5 seconds to wake.

Gutsy broke that suspend-to-ram because the newer kernel uses a different memory allocator which doesn't work well with older ATI cards.  

On a newer machine (Pentium D, 2.9 GHz) Linux Mint 4 (gutsy) suspends fine.  About 6 seconds to sleep and about 6 seconds to wake.  Power goes from 120 watts to 4 watts.

You could also get a $200 Walmart/Everex/Via C7 machine that draws 12 to 20 watts.  At  11 cents/kilowatt it will pay for itself after 3 years of use when used 5-days a week.

---

### Post by ChrisMP1 on 2008-01-21
I have a Dell Dimension 2400. Usually suspend works, but sometimes the computer resumes to a black X screen (all black, mouse pointer in the middle, unresponsive). Is there any way to make sure it works, or any known reason as to why it doesn't?

---

### Post by henriquemaia on 2008-01-22
> **ChrisMP1 said:**
> I have a Dell Dimension 2400. Usually suspend works, but sometimes the computer resumes to a black X screen (all black, mouse pointer in the middle, unresponsive). Is there any way to make sure it works, or any known reason as to why it doesn't?

Check if any of the options of /etc/default/acpi-support can make any difference. On mine does.

Try changing POST_VIDEO=True to false and SAVE_VBE_STATE=True to false also.

---

### Post by ChrisMP1 on 2008-01-22
Problem solved. Thanks!

```
$ diff /etc/default/acpi-support{.bak,}

10c10
< ACPI_SLEEP_MODE=mem
---
> ACPI_SLEEP_MODE=standby
23c23
< SAVE_VBE_STATE=true
---
> SAVE_VBE_STATE=false
26c26
< VBESTATE=/var/lib/acpi-support/vbestate
---
> # VBESTATE=/var/lib/acpi-support/vbestate
29c29
< POST_VIDEO=true
---
> POST_VIDEO=false
42c42
< # DOUBLE_CONSOLE_SWITCH=true
---
> DOUBLE_CONSOLE_SWITCH=true

```

---

