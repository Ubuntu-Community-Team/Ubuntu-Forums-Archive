---
title: "[SOLVED] system restarts when trying to suspend"
date: 2008-07-02
forum: Hardware
---

### Post by john.ennew on 2008-07-02
Hi, 

I just installed a Hauppauge PCI digital TV tuner into my system. Now when I try and suspend to S3 it restarts. I did a complete reinstall of Ubuntu 8.04 to see if this would cure it but it still does it.  I tried a vanilla install and then did a full system update to the latest kernel etc and both exhibit the problem.

How can I go about diagnosing the fault? I had a search round the internet but couldn't find anyone else with the same problems.
```

cat /var/log/pm-suspend.log
Wed Jul  2 23:12:46 BST 2008: running suspend hooks.
===== Wed Jul  2 23:12:46 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Wed Jul  2 23:12:46 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Wed Jul  2 23:12:46 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Wed Jul  2 23:12:46 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
kernel.acpi_video_flags = 0
===== Wed Jul  2 23:12:46 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Wed Jul  2 23:12:46 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Wed Jul  2 23:12:46 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Wed Jul  2 23:12:47 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Wed Jul  2 23:12:47 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Wed Jul  2 23:12:47 BST 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Wed Jul  2 23:12:47 BST 2008: done running suspend hooks.

```

Many thanks,
John

---

### Post by john.ennew on 2008-07-04
I managed to stop the restart on suspend by disabling "Wake on PCI device" in the BIOS.

I was worried this would stop Wake on LAN as there isn't a separate option for this in my mainboards BIOS, however, this still appears to work.

Weird?!

---

