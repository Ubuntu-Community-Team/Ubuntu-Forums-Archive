---
title: "[SOLVED] Synchronizing Rainlendar Calendars Between Partitions"
date: 2008-07-30
forum: General Help
---

### Post by ivansf92 on 2008-07-30
Does anyone know how to synchronize the Default.ics files between Ubuntu Linux and Windows XP partitions or if it is possible or not?

The directories, at least for my computer, are listed below for convenience.

/home/family/.config/.rainlendar2/Default.ics
C:\Documents and Settings\Family\.rainlendar2\Default.ics

But from the Ubuntu partition, the Default.ics file for the Windows partition is located here:

/media/disk/Documents and Settings/Family/.rainlendar2/Default.ics

---

### Post by ivansf92 on 2008-08-11
For anyone in the future who might encounter the same problem, here's how to solve it:

[LIST=1]
[*]Choose which .ics file you want to be synchronized. (Basically, I'm showing you how to use only one .ics file between two or more partitions.) For most of you, it will be the Windows partition because Ext2/3 file systems, by default, cannot be read in Windows. If you want Windows to be able to have full access to Linux Ext2 volumes, then go to [http://www.fs-driver.org/](http://www.fs-driver.org/). Then download and install "Ext2 Installable File System".
[*]Go to the calendars section in options.
[*]Add the .ics file. (You should know where to locate them based on my previous post.)
[*]Under settings after clicking the calendar you have just added, change the value of "Monitor changes" to true on the partition that does not have the .ics file or all of the partitions.
("Monitor changes checks the calendar file and if it changes it will be reloaded automatically. This works on in Windows.")
[/LIST]

---

