---
title: "Ubuntu 5.04 on Inspiron 1000"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by krrh on 2005-04-21
Is anyone using Ubuntu on this machine? I've struggled for the past week trying to overcome two deal-breaking annoyances between this OS and computer. I've corrected one but am searching for help regarding the other.

First, the laptop came with a Broadcom-based wifi card. After much reading the problem is now solved. For anyone else trying to tackle the feat, this [thread](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom)  contains the only HOWTO needed to get the job done. (The "much reading" was necessary only because of many user errors.)

The remaining problem involves ACPI events. The computer responds to sleep and suspend commands. Sometimes the computer will slip itself into these states when asked. Most of the time, however, it does not, in which case the machine locks up. When trying to resume, I find the machine has not complied -- every time -- again, locking up. I've read the HOWTOs, edited menu.lst with resume=/dev/hda6, and debugged the system's DSDT (only a warning here; no errors). It simply isn't working. 

My battery meter reports accurately and reponds when the system switches to AC power.

The last peculiar behavior I've observed with ACPI is that it somehow interferes with  fn keys. Sound, monitor brightness, etc., will work, however, multiple key presses won't register. For example, when I hit the brightness button several times to move up or down multiple steps in LCD brightness, the computer only registers the first press and ignores the rest. When ACPI is disabled at boot, this problem disappears.

So, group, any ideas to help me diagnose the problem?

Thanks.

---

