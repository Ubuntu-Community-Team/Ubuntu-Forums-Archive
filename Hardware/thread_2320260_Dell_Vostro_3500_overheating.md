---
title: "Dell Vostro 3500 overheating"
date: 2016-04-12
forum: Hardware
---

### Post by saeger2 on 2016-04-12
I have a Dell Vostro 3500 laptop that is running wicked hot, around 160 idling and up to 190 or more until it triggers the auto shutdown.  The airflow is unobstructed, there are no fan settings in BIOS. The fan speed does change with usage, but is not enough to keep the temperatures reasonable.  How can I change the temperature thresholds for the different fan speeds to provide more aggressive cooling?

Thanks!

---

### Post by weatherman2 on 2016-04-12
If your laptop is getting that hot, you have another problem besides fan speed, unless the fan is not actually working, but it sounds like the fan is working.

When you say "the airflow is unobstructed," do you mean you have physically taken the laptop apart to clean out the heat sink?  If not, that's probably what you need to do.  That laptop is a few years old.  The last Dell of that vintage I cleaned out had almost a little carpet of lint and dirt blocking the heat sink inside.  Once I cleaned it out, it ran cool and quiet.

Look on Dell's website for a service manual showing you exactly how to take it apart.  Sometimes it's easy - depends on the design of the laptop.  Sometimes you have to take the thing almost completely apart.  You may also do a web search for disassembly instructions or even videos.

---

### Post by saeger2 on 2016-04-12
I found the problem when I realized that the fan spun faster on startup then it did when Xubuntu was running.  Xubuntu's fan control would not turn the fan up all the way.  Changing 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to


GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi.power_nocheck=1"

In /etc/default/grub fixed it.  It now idles at 120F and runs around 150F

---

