---
title: "Hardware control (help needed)"
date: 2010-05-28
forum: Hardware
---

### Post by arvigeus on 2010-05-28
Hello to you, guys, I will need lots of help from you...

I'm writing a program for controlling various hardware components on laptops. Currently it supports EEEPC only, but it could easily get extended if you help me. Since I don't have other laptop to test things, could you assist me (just with info, nothing to install)?

Let's start...

How is usually hardware controlled? For example on eeepc I write some value to a file and/or modprobe some module to toggle the device. Is it the same principle with other similar devices? And where their control files are stored? For example camera control file for eeepc is stored in "/sys/devices/platform/eeepc/camera". What about other laptops? (acer, lenovo, etc)

How can I check if device exists for real? For now I just check for control files and/or lspci. This kinda works, but there is no way to detect the device if it is disabled, even if it works (applies for lsmod, iwconfig and lspci). Is there any reliable way to detect the required modules? The only idea I've got is to load all specific modules and look for device to appear somewhere. Never tested it though...

CPU scaling: All I need for Atom processor is to edit a file in /cpufreq folder. But some processors require some modules to be loaded (I think P4 and Celeron required p4_clockmod). Also, when do I need cpufreq_ondemand and etc. modules? I see they are no longer needed in Lucid. In other distros I should only test if the modules exist and then modprobe them, right? Another thing that bothers me is powernowd. Is there any complete guide how to control it? The ones I found are incomplete. If I have powernowd, will I have a dir cpufreq in /sys/devices/system/cpu/cpu* (weird question, I know)?

Which modules are needed for cpu scaling of different cpu models?

More questions later... (if you answer me these questions)

---

