---
title: "udev rule fails to exec"
date: 2010-01-17
forum: Hardware
---

### Post by mlohmiller on 2010-01-17
I have created the following rule in the /etc/udev/rules.d folder and named the file 95-usbsync.rules

SUBSYSTEM=="block", ATTRS{model}=="S9", RUN+="/home/frohike/s9sync"

The script s9sync runs an rsync command which I have ran outside of the udev rule and it works without an issue.  I have changed the file permissions to 777 so that is not preventing the problem.  It won't run or fails to run (as the syslog says) when I connect the device.  So, from my limited knowledge, my rule arguments are accurately identifying the hardware and attempting to the run the command but this is the output from the syslog. (I bolded the failed line). 

If anyone needs more information I can supply it ASAP. 
Thank you
mlohmiller


Jan 17 17:20:50 frohike-desktop kernel: [13885.013996] scsi 18:0:0:0: Direct-Access     COWON    S9               1.00 PQ: 0 ANSI: 0
Jan 17 17:20:50 frohike-desktop kernel: [13885.014528] sd 18:0:0:0: Attached scsi generic sg4 type 0
Jan 17 17:20:50 frohike-desktop kernel: [13885.015653] sd 18:0:0:0: [sdd] 64569344 512-byte logical blocks: (33.0 GB/30.7 GiB)
Jan 17 17:20:50 frohike-desktop kernel: [13885.027726] sd 18:0:0:0: [sdd] Write Protect is off
Jan 17 17:20:50 frohike-desktop kernel: [13885.027734] sd 18:0:0:0: [sdd] Mode Sense: 37 00 00 08
Jan 17 17:20:50 frohike-desktop kernel: [13885.027739] sd 18:0:0:0: [sdd] Assuming drive cache: write through
Jan 17 17:20:50 frohike-desktop kernel: [13885.043768] sd 18:0:0:0: [sdd] Assuming drive cache: write through
Jan 17 17:20:50 frohike-desktop kernel: [13885.043780]  sdd:
Jan 17 17:20:50 frohike-desktop kernel: [13885.060537] sd 18:0:0:0: [sdd] Assuming drive cache: write through
Jan 17 17:20:50 frohike-desktop kernel: [13885.060547] sd 18:0:0:0: [sdd] Attached SCSI removable disk
**Jan 17 17:20:50 frohike-desktop udevd-work[5769]: exec of program '/home/frohike/s9sync' failed**
Jan 17 17:20:50 frohike-desktop init: ureadahead-other main process (5770) terminated with status 2

---

### Post by falconindy on 2010-01-17
Looks to me like the script is executed before the drive is assigned a mount point. You might need to flesh out the udev rule to assign it a static mount point such as...

```
ACTION=="add", RUN+="/bin/mount -o mountopt1,mountopt2 /dev/%k /media/mount_it_here"
```

I'll let you figure out where you want it mounted and with what options.

Also, you should add a conditional at the top to weed out anything that isn't what you're looking for device-wise...

```
KERNEL!="sd[a-z][0-9]", GOTO="usbsync_rules_end"
ACTION=="add", ATTRS{model}=="S9", RUN+="/bin/mount -o mountopt1,mountopt2 /dev/%k /media/mount_it_here", RUN+="/home/frohike/s9sync"
LABEL="usbsync_rules_end"
```

---

### Post by mlohmiller on 2010-01-17
Thank you so much for the information.  I have not tested it yet.  I will try it shortly. The part that you said to add to prevent other devices from running this, by using sd"[a-z][0-9]"  since my cowon gets added on /dev/sdd won't that exclude my cowon from getting the command to run.  Not questioning you just hoping I learn a little more from you and understand how they udev rules work.  

Thanks in advanced.

mlohmiller

---

### Post by falconindy on 2010-01-17
> **mlohmiller said:**
> Thank you so much for the information.  I have not tested it yet.  I will try it shortly. The part that you said to add to prevent other devices from running this, by using sd"[a-z][0-9]"  since my cowon gets added on /dev/sdd won't that exclude my cowon from getting the command to run.  Not questioning you just hoping I learn a little more from you and understand how they udev rules work.  

Thanks in advanced.

mlohmiller
Even a device with only one partition will have a partition number associated with it, and as such you will mount the partition (which fits the regex sd[a-z][0-9]) **not** the device.

---

### Post by mlohmiller on 2010-01-19
Sorry for the delay.  I got caught up in an emergency consulting issue and have been MIA for days.

It seems to still be a problem even with the specified mount rule.
Please let me know if I am doing something really brain dead here. Also the permissions on the file are 777 owners are root:root.  Not sure if that matters.

**_Here is the new rule. _**
ACTION=="add", RUN+="/bin/mount -o auto /dev/%k /media/COWON\ S9/"
SUBSYSTEM=="block", ATTRS{model}=="S9", RUN+="/home/frohike/s9sync"

_**Here is the syslog**_
Jan 19 14:27:53 frohike-desktop kernel: [176307.994384] usb 1-6: configuration #1 chosen from 1 choice
Jan 19 14:27:53 frohike-desktop kernel: [176307.994686] scsi19 : SCSI emulation for USB Mass Storage devices
Jan 19 14:27:53 frohike-desktop kernel: [176307.994806] usb-storage: device found at 13
Jan 19 14:27:53 frohike-desktop kernel: [176307.994812] usb-storage: waiting for device to settle before scanning
Jan 19 14:27:58 frohike-desktop kernel: [176312.991699] usb-storage: device scan complete
Jan 19 14:27:58 frohike-desktop kernel: [176312.993776] scsi 19:0:0:0: Direct-Access     COWON    S9               1.00 PQ: 0 ANSI: 0
Jan 19 14:27:58 frohike-desktop kernel: [176312.994910] sd 19:0:0:0: Attached scsi generic sg3 type 0
Jan 19 14:27:58 frohike-desktop kernel: [176312.995879] sd 19:0:0:0: [sdd] 64569344 512-byte logical blocks: (33.0 GB/30.7 GiB)
Jan 19 14:27:58 frohike-desktop kernel: [176313.007995] sd 19:0:0:0: [sdd] Write Protect is off
Jan 19 14:27:58 frohike-desktop kernel: [176313.008003] sd 19:0:0:0: [sdd] Mode Sense: 37 00 00 08
Jan 19 14:27:58 frohike-desktop kernel: [176313.008007] sd 19:0:0:0: [sdd] Assuming drive cache: write through
Jan 19 14:27:58 frohike-desktop kernel: [176313.023696] sd 19:0:0:0: [sdd] Assuming drive cache: write through
Jan 19 14:27:58 frohike-desktop kernel: [176313.023707]  sdd:
Jan 19 14:27:58 frohike-desktop kernel: [176313.039401] sd 19:0:0:0: [sdd] Assuming drive cache: write through
Jan 19 14:27:58 frohike-desktop kernel: [176313.039410] sd 19:0:0:0: [sdd] Attached SCSI removable disk
Jan 19 14:27:58 frohike-desktop kernel: [176313.120238] FAT: bread failed in fat_clusters_flush
Jan 19 14:27:59 frohike-desktop kernel: [176313.325873] FAT: bread failed in fat_clusters_flush
Jan 19 14:27:59 frohike-desktop kernel: [176313.325890] FAT: bread failed in fat_clusters_flush
Jan 19 14:27:59 frohike-desktop udevd-work[12952]: exec of program '/home/frohike/s9sync' failed
Jan 19 14:27:59 frohike-desktop init: ureadahead-other main process (12953) terminated with status 2

---

### Post by mlohmiller on 2010-01-19
Got it to work.  

You need a shebang with shell at the beginning of the script
#!/bin/bash
I am not sure if this is handled differently, but I also renamed it with a .sh extension. 
I found an site that said if you are running a script for shell commands you need to specify a shebang
Thanks for all the help!!!!!  I may start a new thread if need to help with the deny components of the udev rule.
"udev does not run these programs on any active terminal, and it does not execute them under the context of a shell. Be sure to ensure your program is marked executable, if it is a shell script ensure it starts with an appropriate [shebang]("http://en.wikipedia.org/wiki/Shebang_%28Unix%29") (e.g. #!/bin/sh), and do not expect any standard output to appear on your terminal."
[http://reactivated.net/writing_udev_rules.html#builtin](http://reactivated.net/writing_udev_rules.html#builtin)

---

