---
title: "How do I underclock the CPU?"
date: 2008-08-09
forum: Hardware
---

### Post by mlinchits on 2008-08-09
I want underclock the 1.7 Ghz CPU on my Thinkpad (I can't bear its awful fan noise). Since I am in Gnome I've tried the "Scaling Monitor" and "Emifreq" panel applets, but changing the settings in their drop down menus does nothing to the CPU frequency. I thentried changing the settings in BIOS and now my CPU runs at a constant 1.4 Ghz. Is it possible to go lower than that or to have the CPU alternate between say 0.8 and 1.4 depending on demand? If so, could anyone please recommend an app/solution?

By the way here a console output - not sure if contains any useful info:

mlinchits@MIBM:~$ lsmod | grep acpi_cpufreq
acpi_cpufreq           10796  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
processor              36872  3 acpi_cpufreq,thermal


Thanks,
Max

---

### Post by kajillin on 2008-08-09
if its not in your bios, your manufacturer see's it unsafe to do so! And if your sick of the sound of your fan now wait till you overclock ....... and your fan no longer works, thatll probly piss you off even more.

---

### Post by mlinchits on 2008-08-09
Well no, I can adjust the power settings in BIOS down to a constant 1.4 Ghz. Under the default settings my CPU occasionally runs at 0.6 so scaling it down is possible. I'd want to underclock, *not overclock*. Help?

thanks

---

### Post by mlinchits on 2008-08-09
I've moved this thread to absolute beginner talk as the issue does not pertain to hardware detection.

---

### Post by sdennie on 2008-08-09
> **mlinchits said:**
> I've moved this thread to absolute beginner talk as the issue does not pertain to hardware detection.

This is a reasonable sub-forum for this thread.

Have you tried using cpufreq-info and cpufreq-selector to change the frequencies?  That may not completely eliminate the need for a fan but, the more power savings features you enable (incidentally, underclocking the CPU doesn't generally save power), the less heat that is generated and so less time with the fan on.  You may want to have a look at [www.lesswatts.org](www.lesswatts.org) and some of the links in my signature.  Though the XPS m1330 link doesn't directly relate to your laptop, using that thread keeps my laptop so cool that the fan stays off for long periods of time.

---

