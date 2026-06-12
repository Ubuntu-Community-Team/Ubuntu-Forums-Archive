---
title: "Wubi installation failed"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by haal on 2009-03-15
Hi all, 
I'm trying to install Xubuntu from Wubi. When i reboot to complete the installation, near the end of the install it gives me the error 'No root file system is defined. Please correct this from the partitions.' and then this messagebox keeps appearing forever no matter how many times i close it.
So I just revert to console mode and reboot.

This is the end of /var/message/log at the point when the installation hangs:

```

Mar 15 17:23:57 ubuntu ubiquity: Your console font configuration will be updated the next time your system
Mar 15 17:23:57 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Mar 15 17:23:57 ubuntu ubiquity[7309]: log-output -t ubiquity setxkbmap -model pc105 -layout it -option  -option 
Mar 15 17:23:57 ubuntu ubiquity[7309]: Step_before = stepLanguage
Mar 15 17:24:00 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: 
Mar 15 17:24:00 ubuntu ubiquity: /lib/partman/choose_partition/Finish: not found
Mar 15 17:24:00 ubuntu ubiquity: 
Mar 15 17:24:03 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: 
Mar 15 17:24:03 ubuntu ubiquity: /lib/partman/choose_partition/Finish: not found
Mar 15 17:24:03 ubuntu ubiquity: 
Mar 15 17:24:05 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: 
Mar 15 17:24:05 ubuntu ubiquity: /lib/partman/choose_partition/Finish: not found
Mar 15 17:24:05 ubuntu ubiquity: 
Mar 15 17:24:05 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: 
Mar 15 17:24:05 ubuntu ubiquity: /lib/partman/choose_partition/Finish: not found
Mar 15 17:24:05 ubuntu ubiquity: 
Mar 15 17:24:06 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: 
Mar 15 17:24:06 ubuntu ubiquity: /lib/partman/choose_partition/Finish: not found
Mar 15 17:24:06 ubuntu ubiquity: 
Mar 15 17:24:06 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: 
Mar 15 17:24:06 ubuntu ubiquity: /lib/partman/choose_partition/Finish: not found
Mar 15 17:24:06 ubuntu ubiquity: 
Mar 15 17:24:07 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: 
Mar 15 17:24:07 ubuntu ubiquity: /lib/partman/choose_partition/Finish: not found
Mar 15 17:24:07 ubuntu ubiquity: 
Mar 15 17:24:08 ubuntu kernel: [   75.446589] [drm] Num pipes: 2
Mar 15 17:26:06 ubuntu kernel: [  193.503024] [drm] Loading R400 Microcode
Mar 15 17:26:06 ubuntu kernel: [  193.503075] [drm] Num pipes: 2
Mar 15 17:26:08 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: 
Mar 15 17:26:08 ubuntu ubiquity: /lib/partman/choose_partition/Finish: not found
Mar 15 17:26:08 ubuntu ubiquity: 
Mar 15 17:26:08 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: 
Mar 15 17:26:08 ubuntu ubiquity: /lib/partman/choose_partition/Finish: not found
Mar 15 17:26:08 ubuntu ubiquity: 
Mar 15 17:26:09 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: 
Mar 15 17:26:09 ubuntu ubiquity: /lib/partman/choose_partition/Finish: not found
Mar 15 17:26:09 ubuntu ubiquity: 
Mar 15 17:26:10 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: 
Mar 15 17:26:10 ubuntu ubiquity: /lib/partman/choose_partition/Finish: not found
Mar 15 17:26:10 ubuntu ubiquity: 
Mar 15 17:26:11 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: 
Mar 15 17:26:11 ubuntu ubiquity: /lib/partman/choose_partition/Finish: not found
Mar 15 17:26:11 ubuntu ubiquity: 
Mar 15 17:26:11 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: 
Mar 15 17:26:11 ubuntu ubiquity: /lib/partman/choose_partition/Finish: not found


```

I suspect the error line of interest is "ubiquity: /lib/partman/choose_partition/Finish: not found
" but there is no explanation on google about this error.

I already tried to uninstall wubi run chdisk on the partition and reinstall again, but with the same error showing again.
Did anyone face this problem before ?

---

### Post by haal on 2009-03-15
I also tried the defragmentation of the partition but still the same problem!!!
Can anyone help me??

---

### Post by haal on 2009-03-16
up!

---

### Post by haal on 2009-03-16
up!

---

### Post by haal on 2009-03-17
Bump!

---

