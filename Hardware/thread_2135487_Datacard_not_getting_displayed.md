---
title: "Datacard not getting displayed"
date: 2013-04-14
forum: Hardware
---

### Post by Anoop Jose on 2013-04-14
Hi,
 i have memory card of 4 GB. when i connect the same to windows system, it tells to format the card to use. in ubuntu id doesnt shw. i ve valuable data in that drive . how can i extract it?

ubuntu@ubuntu:~$ lsusb
Bus 001 Device 007: ID 14cd:125c Super Top 
Bus 001 Device 003: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 004 Device 002: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 004 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~$

---

### Post by prshah on 2013-04-14
Is the memory card at all usable? Open a terminal, and give the command ```
tail -f /var/log/syslog
``` Now, plug in your memory card (USB pen drive?), and you should notice a number of new lines appearing on the terminal. Please copy and paste these lines here, to help diagnose the problem.

If the memory card is at all recognized, you can use the testdisk suite (testdisk for partition recovery, and/or photorec for recovery of individual files). Testdisk suite is available in the software repos, and can be installed with the terminal command```
sudo apt-get install testdisk
```

---

### Post by Anoop Jose on 2013-04-18
with memory card plugged in
arun@arun-desktop:~$ tail -f /var/log/syslog
Apr 18 11:25:18 arun-desktop kernel: [  170.472644] sd 6:0:0:0: [sdb] Write Protect is off
Apr 18 11:25:18 arun-desktop kernel: [  170.472648] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
Apr 18 11:25:18 arun-desktop kernel: [  170.473218] sd 6:0:0:0: [sdb] No Caching mode page present
Apr 18 11:25:18 arun-desktop kernel: [  170.473223] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Apr 18 11:25:18 arun-desktop kernel: [  170.476251] sd 6:0:0:0: [sdb] No Caching mode page present
Apr 18 11:25:18 arun-desktop kernel: [  170.476256] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Apr 18 11:25:18 arun-desktop kernel: [  170.478928]  sdb: unknown partition table
Apr 18 11:25:18 arun-desktop kernel: [  170.481154] sd 6:0:0:0: [sdb] No Caching mode page present
Apr 18 11:25:18 arun-desktop kernel: [  170.481159] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Apr 18 11:25:18 arun-desktop kernel: [  170.481162] sd 6:0:0:0: [sdb] Attached SCSI removable disk

---

### Post by Anoop Jose on 2013-04-18
without memory card
arun@arun-desktop:~$ tail -f /var/log/syslog
Apr 18 11:25:18 arun-desktop kernel: [  170.473223] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Apr 18 11:25:18 arun-desktop kernel: [  170.476251] sd 6:0:0:0: [sdb] No Caching mode page present
Apr 18 11:25:18 arun-desktop kernel: [  170.476256] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Apr 18 11:25:18 arun-desktop kernel: [  170.478928]  sdb: unknown partition table
Apr 18 11:25:18 arun-desktop kernel: [  170.481154] sd 6:0:0:0: [sdb] No Caching mode page present
Apr 18 11:25:18 arun-desktop kernel: [  170.481159] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Apr 18 11:25:18 arun-desktop kernel: [  170.481162] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Apr 18 11:27:35 arun-desktop kernel: [  307.858253] usb 1-1: USB disconnect, device number 9
Apr 18 11:27:42 arun-desktop anacron[938]: Job `cron.daily' started
Apr 18 11:27:42 arun-desktop anacron[2348]: Updated timestamp for job `cron.daily' to 2013-04-18

---

