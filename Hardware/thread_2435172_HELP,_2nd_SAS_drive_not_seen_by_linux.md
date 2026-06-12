---
title: "HELP, 2nd SAS drive not seen by linux"
date: 2020-01-17
forum: Hardware
---

### Post by alphanumeric01 on 2020-01-17
I have a 120G OCZ Revodrive 3 (2*60G SAS drives) which I bought recently. Only the second drive is seen by UEFI/BIOS on startup. There is a message about a checksum error for the first drive. Only the second drive is identified using lsblk and similar commands. Previous owner has installed a 2.50 firmware on the drive but only 2.25 is listed as most recent available using OCZ/Toshiba utility. When I try to downgrade firmware to 2.25 it says 'SCSI transport failed'.

Is there a way to find an identifier for the first drive in order to force flash the correct firmware and try to correct this checksum error? Hopefully then I'll be able to access the first drive.

Also, I'm new to linux and terminal commands so please detail whatever switches etc to be used with commands.

Thanks in advance.

---

### Post by TheFu on 2020-01-17
I don't know the answer.

You'll need to use manpages to learn how to accomplish what you seek.
The tools to gather information are **hdparm** and **smartctl**. I think both will need to be installed, since they aren't usually included for normal desktop distros.

```
man hdparm
```

Some firmware cannot be downgraded. You might be stuck. Contact the vendor.

If there are HW issues, you'll want to check the system logs to determine what might be the cause and correct that. _SCSI transport failed_ could be lots of hardware issues. Bad cable, bad HBA, bad disk, bad/insufficient PSU.  **dmesg** is the boot log. Search that output.

There is a manpage for every command on the system which explains how to use each command. There are common patterns for most that only experience can teach.

I would start by gathering data with something like this:
```
$ sudo hdparm -I /dev/sdZ
```
You'll need to figure out the specific device to be used.  [https://www.tldp.org/HOWTO/Partition-Mass-Storage-Definitions-Naming-HOWTO/x99.html](https://www.tldp.org/HOWTO/Partition-Mass-Storage-Definitions-Naming-HOWTO/x99.html) explains storage device names.  Be aware that the name for a partition is tied to the name of the whole drive, but NOT the same.  Partitions matter, if that is what is needed.  Unix will let us treat a drive like a partition or a partition like a drive. Usually, this is a bad idea, but nothing will stop a user from doing it, since in some situations it might be a great idea.  This is a different philosophy than other OSes.  "Can is be done?", not "Should it be allowed?" is the only questions.  Since almost everything on a Unix system is a file deep down, almost anything on a Unix system can be treated like a file.  This is genius or a recipe for disaster to the uninformed.

---

