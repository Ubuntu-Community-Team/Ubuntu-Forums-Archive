---
title: "Unable to partition hard drive?"
date: 2015-03-15
forum: Hardware
---

### Post by Matthew_Stephenson on 2015-03-15
Hello everyone, I've been having a slight problem with my new hard drive. I cant format, or partition it. Trying to do so in GParted gives me this error:
> [COLOR=#000000][FONT=Times New Roman]GParted 0.18.0 --enable-libparted-dmraid --enable-online-resize[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman]Libparted 2.3[/FONT][/COLOR]
[TABLE]
[TR]
[TD="colspan: 2"]**Format /dev/sdb1 as ntfs**  00:01:12    ( ERROR )[/TD]
[/TR]
[TR]
[TD]    [/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"]calibrate /dev/sdb1  00:00:29    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD]    [/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"][I]path: /dev/sdb1
start: 2048
end: 1953523711
size: 1953521664 (931.51 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]clear old file system signatures in /dev/sdb1  00:00:43    ( ERROR )[/TD]
[/TR]
[TR]
[TD]    [/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"]write 68.00 KiB of zeros at byte offset 0  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]write 4.00 KiB of zeros at byte offset 67108864  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]write 4.00 KiB of zeros at byte offset 274877906944  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]write 4.00 KiB of zeros at byte offset 1000203087872  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]flush operating system cache of /dev/sdb  00:00:15    ( ERROR )[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]libparted messages    ( INFO )[/TD]
[/TR]
[TR]
[TD]    [/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"]*Input/output error during write on /dev/sdb*[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[COLOR=#000000][FONT=Times New Roman]========================================[/FONT][/COLOR]
Any ideas?

Thanks,

---

### Post by Mark Phelps on 2015-03-16
How are you trying to do this? Are you running Gparted from the command line? OR, are you using the GUI and selecting options in it?

Also, I would try running fdisk from the command line to see what it thinks of the drive: "sudo fdisk -lu" (lowercase L, not a one).

---

