---
title: "Pushed suspend... no more laptop???"
date: 2007-09-21
forum: Hardware &amp; Laptops
---

### Post by tippiecup on 2007-09-21
I'm running Fiesty on an Emachine 5312 laptop.  I clicked Suspend, and sure enough it went into suspend mode, but I can't get it out of suspense no matter what I try.  My screen is blank, no hard drive activity, system fan is running, but I get no responce to any button I push.  Held down the power botton for a few seconds and the machine seems to power all the way off... push it again and right back into suspend mode.... nothing seems to work....Can Anyone tell me what to do????  How do I wake it up? Reboot?  Force Crash?   This is worse than losing everthing on the hard drive.  I can't even start over...it just sitsd there!!!!!!???????

---

### Post by roxy99 on 2007-09-21
First take out the hard drive and go to a data recovery service and get your data backed up onto a new hard drive.  Chances are the data is all intact.  Next, try to boot up without the batterypack and get into the bios (F1 or Del to enter setup at the splash screen).  Hopefully you can get into the bios.  Try to find ACPI or power mangement and disable it from the bios.  Save settings and reboot.

Good luck it sounds like a real shame.

---

### Post by MrHippocampus on 2007-09-21
If the machine is on, try the [emergency reboot]("http://en.wikipedia.org/wiki/Magic_SysRq_key#Emergency_reboot") procedure, that should hopefully cleanly restart the machine.

---

### Post by tippiecup on 2007-09-21
Thanks, I just tried the sugestion above it seemed to work.    I glad I didn't have to take out and backup the drive.   But I think I will disable ACPI .....THANKS AGAIN

---

### Post by tippiecup on 2007-09-21
Thanks SO MUCH for the Help....I was just about beside myself with frustration....emergency shutdown  and reboot .... and back on!    Whew!

Thanks again so much!!!!

---

### Post by MrHippocampus on 2007-09-21
You probably shouldn't disable ACPI unless its causing other problems with your machine, just steer clear of the suspend button is my advice :)

---

### Post by IcemanV9 on 2007-09-21
I second MrHippocampus's suggesstion: Do NOT disable ACPI; just don't use suspend at all. I am glad that you did not lose any data. :-)

---

### Post by roxy99 on 2007-09-21
> **IcemanV9 said:**
> I second MrHippocampus's suggesstion: Do NOT disable ACPI; just don't use suspend at all. I am glad that you did not lose any data. :-)

You're probably right.  Once you disable it there's proabably no way to re-activate without making a mess.  I just suggested that as a last resort. Thats a great trick the emergency shutdown procedure.   On my laptop the ACPI was diabled by default during setup because my bios is pre-2000.  I don't worry about the enrgy and powersaving modes because its always plugged in so I do without ACPI.  However, disabling could cause problems in the HAL thay would be even more problematic than the buggy suspend mode.

---

### Post by tippiecup on 2007-09-22
> **roxy99 said:**
> You're probably right.  Once you disable it there's proabably no way to re-activate without making a mess.  I just suggested that as a last resort. Thats a great trick the emergency shutdown procedure.   On my laptop the ACPI was diabled by default during setup because my bios is pre-2000.  I don't worry about the enrgy and powersaving modes because its always plugged in so I do without ACPI.  However, disabling could cause problems in the HAL thay would be even more problematic than the buggy suspend mode.

OK thanks!   is there a way to remove the suspend button from the "exit" menu?

---

