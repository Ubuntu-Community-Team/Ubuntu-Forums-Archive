---
title: "Disk full due to large .xsession-errors(deleted) open file applications"
date: 2013-05-28
forum: Hardware
---

### Post by Cambysese on 2013-05-28
My root disk is full to the brim because of, I suspect, disk space locked up by a ballooning /home/user/.xsession-errors file. The ballooning is caused by open processes, i.e., PID from several different applications e.g., chromium being the largest culprit. I suspect this is the case becuase ```
lsof | grep deleted
``` returns lines like:
[I]
chromium- 27607  ktavabi  2w  REG 8,1 1809493864448  108527952 /home/ktavabi/.xsession-errors (deleted)
chromium- 27762  ktavabi  2w  REG 8,1 1809493864448  108527952 /home/ktavabi/.xsession-errors (deleted)
[/I]
The situation is so bad that I can't even post the others as my terminal cannot find resources to scroll the entire output. The twist is that I have a cron job set to delete the file home/ktavabi/.xsession-errors` as per a suggested work around to the chaotic file size growth associated with it on UBUNTU distros. I am using a 64bit UBUNTU 12.04 machine with the following HD config:
[I]
Filesystem      Size  Used Avail Use% Mounted on
    /dev/sda1       1.8T  1.7T     0 100% /
    udev             12G  4.0K   12G   1% /dev
    tmpfs           4.8G  1.3M  4.8G   1% /run
    none            5.0M   48K  5.0M   1% /run/lock
    none             12G  2.0M   12G   1% /run/shm
[/I]
My questions are (1) How can I reclaim this space? Is rebooting an option? meaning will be able to log back in or just end up with a bloated, dead machine? (2) How do I ensure this doesn't happen again? (3) What is the bloody deal with .xsession-errors? is there a true fix? Is it really the users responsibility to deal with this issue?
Thanks in advance

---

