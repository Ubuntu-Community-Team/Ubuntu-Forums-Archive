---
title: "USB 2-5 device descriptor read/64, error -110 (nothing connected to usb)"
date: 2017-02-24
forum: Hardware
---

### Post by RRoel on 2017-02-24
I am getting an error "USB 2-5 device descriptor read/64, error -110" when trying to boot Ubuntu.
Recently I 'refreshed' Windows and reinstalled Ubuntu (dual boot).
 I am not sure if that has anything to do with it. Everything seemed to work OK for a few weeks.
There are many threads reporting this error, where the issue is supposed to be solved when unplugging all USB devices, shutting down, waiting a bit, and booting again.
Even after leaving my laptop off overnight, without any USB devices connected, the problem persists.
Windows works without problems, and I can boot Ubuntu from a USB drive as well.

[ATTACH=CONFIG]273883[/ATTACH]

Any help would be much appreciated :)

---

### Post by cariboo on 2017-03-02
I'm not sure if it's the same problem, but I was getting the same message a couple of weeks ago. I have a separate /home partition, it it seems the file system was corrupted. To resolve the problem, I restarted in recovery mode, and selected the root prompt option, once at the prompt I ran the following command:

```
fsck /dev/sdb3
```

if /dev/sda6 is the partition you are having problems with, make sure the drive is connected and start in recovery mode, select the root prompt option and run the following command:

```
fsck /dev/sda6
```

---

### Post by RRoel on 2017-03-04
Yes, that solved it, thanks a lot!
I don't have a separate home selection, and I used to get clearer error messages when I needed to run fsck.

---

### Post by RRoel on 2017-05-23
For future reference:
I ran into the problem again, this time because "fast startup**"** somehow got enabled in Windows.
It can be turned of in "Control Panel\All Control Panel Items\Power Options\System Settings" (in Windows)

---

