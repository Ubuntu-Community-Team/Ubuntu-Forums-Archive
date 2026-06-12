---
title: "ACPI, power consumption and &quot;rescheduling interrupts&quot; on DELL XPS M1530"
date: 2008-07-11
forum: Hardware
---

### Post by quantenmetz on 2008-07-11
Hi there,

as I occasionally need to work on my notebook without power supply at the moment for some hours I was looking into my power consumption under Ubuntu 8.04 yesterday for the first time.

I had experienced a very low battery lifetime running Ubuntu before (50% LESS than in VISTA!) but I have never investigated this.

Yesterday I finally installed powertop and found that my wakeups are dominated by this kernel process:

       [B]36.8% (157.4)      <kernel IPI> : Rescheduling interrupts 
[/B]

My power consumption was over 22 Watts! On top of that, I noticed that the ACPI power estimate inside powertop did not work.
I googled a lot and found out that the "rescheduling interrupts" issue could be caused by faulty ACPI management. 
Following a comment from a Ubuntu forum I tried the acpi=noirq boot option. This cut down my power consumption to 10 Watts and the kernel process caused only like 10% of the wakeups anymore. However, USB, sound and WiFi were not working.
Rebooting without the acpi=noirq option brought everything back to normal. However, NOW I can see the ACPI power estimates inside powertop, that didn't work before. Stuff like that almost reminds me of the old Windows 98 times...

I really want to know what's going on. With disabled Bluetooth and some other tweaks my good friend powertop told me I am down to roughly 19 Watts (lowest display brightness, no dessktop effects...) but the "rescheduling interrupts" process still causes up to several hundreds of wakeups. 

Has anybody any experience with this problem? And is there any experience concerning general power consumption levels of the XPS 1530 under Ubuntu?

Thanks for the help!

Felix

---

### Post by atlas95 on 2008-07-11
Same problem on the m1330 and with acpi=noirq this is good ! but at boot before usplash i can see some error but i can read them :/

---

