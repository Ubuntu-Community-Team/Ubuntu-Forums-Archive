---
title: "HP DV1000 Laptop Resume settings and other settings"
date: 2007-12-07
forum: Hardware &amp; Laptops
---

### Post by medisoft on 2007-12-07
Hi! I wish to make public some parameters that should be included in the next release of ubuntu or in an upgrade.

In my laptop (HP DV1325LA) there are some settings that improves functionality and also make it look nicer.

First, before going to sleep, it needs to set in /proc/acpi/wakeup the events that will wakeup the machine. This is the code
mario@sakura:/etc/acpi/suspend.d$ cat 91-wakeupevents.sh
#!/bin/bash
echo PCIB > /proc/acpi/wakeup
echo PS2K > /proc/acpi/wakeup

with that, if you press a key o touch the touchpad the machine will wake up.

Also, to enable the LED on the Wireless button or in the Mute button you need this on /etc/modprobe.d/options

options ipw2200 led=1
options snd_intel8x0 ac97_quirk=hp_mute_led

That's all :)

---

### Post by inverseroom on 2008-01-27
Thanks for this!  The code for the "wireless" led works flawlessly on my dv1000.  I'm kind of a newb though and don't understand the suspend code.../proc/acpi/wakeup seems to be completely empty and what's with the mario@sakura bit?  Should that go in there too?

I should add that my computer seems to suspend and wake back up fine...my only problem is that the wifi refuses to come back on and I have to reboot.  Does that code fix this problem, or should I be looking elsewhere?

---

