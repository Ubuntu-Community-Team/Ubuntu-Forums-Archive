---
title: "/dev/lp0 &quot;Permission denied&quot;"
date: 2008-10-13
forum: General Help
---

### Post by ubuhauke on 2008-10-13
In my Kubuntu 7.10 I had shared the cups server to the local network by checking the appropriate option the KDE printing control panel. After this, the parallel printer did not work anymore. The IPP report (and /var/log/cups/error_log) showed that the parallel backend could not write to /dev/lp0 anymore. 

The device file had the following permissions:

[FONT="monospace"]crw-rw---- 1 root lp 6, 0 2008-10-13 10:30 /dev/lp0[/FONT]

The solution was to modify /etc/cups/cupsd.conf from

[FONT="monospace"]Group lpadmin[/FONT] 

to 

[FONT="monospace"]Group lp[/FONT]

This ist the group the device and the backend user lp belong to. 

(Don't forget to "/etc/init.d/cupsys restart".)

---

