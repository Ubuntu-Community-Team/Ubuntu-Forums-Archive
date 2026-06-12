---
title: "LG DVD Drive Issue"
date: 2008-06-06
forum: Hardware
---

### Post by nulity on 2008-06-06
[SIZE=2]Hello folks,
this is my first thread,
i have LG dvd+_RW which is not reading/writing discs. 
the "cat /etc/fstab" output is :
=====================================
[/SIZE][SIZE=2][COLOR=DarkRed] # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6e49d64b-743c-4217-95a8-553585bf62aa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f988697f-b761-4e5b-a485-894e94ae9a85 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       [/COLOR][/SIZE][SIZE=2]0
=====================================


when i try to mount the drive from Places -> computer i get :
"[/SIZE]  [SIZE=2][COLOR=DarkRed]Unable to mount media.
There is probably no media in the drive.[/COLOR][/SIZE][SIZE=2]"
but there is CD in that drive, moreover, when i mount the drive from the terminal
using : " [/SIZE][SIZE=2][COLOR=DarkRed]/media/cdrom1[/COLOR][/SIZE][SIZE=2]" i get the following:
[/SIZE][SIZE=2][COLOR=DarkRed][COLOR=Black]"[/COLOR] mount: block device /dev/scd1 is write-protected, mounting read-only [COLOR=Black]"[/COLOR][/COLOR][/SIZE][SIZE=2]
and i was able to navigate thru the content of that CD in terminal, but using the GUI still given 
"[/SIZE][SIZE=2][COLOR=DarkRed]Unable to mount media.....[/COLOR][/SIZE][SIZE=2]"

[/SIZE]  [SIZE=2][COLOR=DarkSlateBlue]
** Any clue about whats the problem and how to solve that issue ?**[/COLOR][/SIZE]

---

### Post by nulity on 2008-06-08
Anyone ????? :(

---

### Post by nulity on 2008-06-09
Where are the experts ? 
plz any one can help, I'm having this issue and i need to burn disks urgently.

---

### Post by Draist on 2008-06-19
I'm having the exact same issue, found any fixes yet?

---

