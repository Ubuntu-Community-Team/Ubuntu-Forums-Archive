---
title: "Laserjet 4L printing problem"
date: 2008-05-03
forum: Hardware
---

### Post by idaspud on 2008-05-03
Hi,

    I have a Hawking HPS3P print server with an HP Laserjet 4L connected to it. Has been working fine in 7.04 and 7.10. I did the upgrade through Updates to 8.04, and aside from a few minor problems, the update went well. However, I lost the ability to print to the Laserjet 4L. The setting is URI lpd://192.168.0.100/lpt2 which works fine in 7.10. Now in 8.04 when I try to print, the printer starts but I am getting garbage printed out. Mostly just thin lines. Occasionally I'll get a partial test print page, but that's it. Removed the printer and reinstalled it through the system-config-printer, but no joy there. I connected the printer directly to the computer and was able to print ok. Moved the printer back to the Hawking and no joy.

 I tried booting to the 8.04 live disk and setting it up there, but with the same result. I booted to the 7.10 live disk and had no problem at all printing. So am I missing something in 8.04, a different setting or something?

Thanks!

---

### Post by idaspud on 2008-05-06
Found this same problem at Launchpad ==> Bugs. (Bug 213081) It's staus is now a "comnfirmed bug," and "Critical." I'll be waiting for a fix. No worries, I just phisically connected the printer to this machine and will use this machine as the print server for the time being.

Cheers

---

