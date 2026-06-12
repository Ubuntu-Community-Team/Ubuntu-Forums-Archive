---
title: "CPU Frequency Scaling"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by xx404 on 2005-10-18
Is there a way to configure Ubuntu to always run on maximum CPU when running on power and to automatically use minimum CPU when running on battery? I've removed powernowd since my laptop pauses every time that the CPU is scaled. The latest version of laptop-mode-tools (from the authors home page) is able to do this but that package doesn't seem to work that well with Breezy.

I'll probably have to write my own ACPI scripts like a true Linux geek won't I?

---

### Post by FLeiXiuS on 2005-10-18
You can disable CPU Frequency Scaling -- I'm not on my laptop so I don't know the actual name of the script.  

It's located in /etc/init.d/ where you can $ chmod -x /etc/init.d/filename.

Give that a shot, then reboot!

---

### Post by xx404 on 2005-10-20
I think the script you are thinking of is the powernowd script. This is the daemon that does on-demand CPU scaling. Disabling it is the first step but since my CPU is old and only has two steps I'm happy to run on full speed when on power and on 80% speed when running on battery. Dynamic scaling doesn't work properly on my laptop (Dell CPxJ750) since the whole system pauses every time it scales, which is really annoying.

I can write an ACPI script that calls cpufreqselector when power is removed/applied but this won't be executed on boot.

Unless someone knows of a way to force ACPI events to be triggered on boot?

---

