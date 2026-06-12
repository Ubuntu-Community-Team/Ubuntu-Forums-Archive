---
title: "CPU fan runs continuously"
date: 2009-11-18
forum: Hardware
---

### Post by mankind117 on 2009-11-18
I have a fairly new HP pavilion e9150t with a quad i7 processor.  I want to dual windows 7
and linux on it.  To make sure this would work I tried running ubuntu off the live CD first.
I can run ubuntu off the live CD with no problems except one that makes me leary
to install a real linux installation on the machine.  I find that when I boot
into ubuntu with the live CD the CPU fan just runs continuously.  I have also found
the same behavior when using the fedora live CD. Does anyone have any ideas why this is
happening or if there is anyway to fix it?

---

### Post by nixscripter on 2009-11-18
Try this command:

```
sudo cpufreq-set -g powersave
```

If things quiet down, then that means that dynamic CPU frequency scaling isn't set right.

If you get "command not found", try installing the **cpufrequtils** package in Synaptic package manager.

---

