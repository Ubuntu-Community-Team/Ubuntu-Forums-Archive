---
title: "[SOLVED] Time keeps changing on my computer."
date: 2008-08-16
forum: General Help
---

### Post by rmjohnson144 on 2008-08-16
I setup a dual boot for Vista Ultimate x64 and Ubuntu 8.04 x64.  I don't use the grub menu and instead use the BIOS to switch when needed as I have a dedicated Vista machine as well as this one.

Anyway, whenever I switch to my Vista hard drive in the BIOS it always sets the clock ahead a few hours (7 hours this time.)  Is there something I can do to fix this, or is this a bug I need to report?

It only happens from Ubuntu to Vista and then vista is screwed up.  If I switch from Vista to Ubuntu then all is fine.  and it happens every single time I switch to Vista.

Thanks
-=Mark=-
ps. I have Ubuntu 8.04 installed on a third drive and it happens with it as well.

edit: I just rebooted and went into the BIOS, and sure enough, the clock was 7 hours ahead again in the BIOS.  I'll post at DFI and see if I can come up with anything.

---

### Post by Ptero-4 on 2008-08-16
You need to change ubuntu from using UTC (which is the default for *NIX systems) to localhost. In that way both 'doze and linux use the same way of handling the clock and hence both keep the time straight.

---

### Post by crasher35 on 2008-11-28
[INDENT]*You need to change ubuntu from using UTC (which is the default for *NIX systems) to localhost. In that way both 'doze and linux use the same way of handling the clock and hence both keep the time straight.*
[/INDENT]
How do you do this?  I'm having the same problem but I don't know how to switch Ubuntu from using UTC to localhost.  I'm on Hardy Heron, btw.

---

### Post by lswb on 2008-11-28
For more than you probably want to know, look at the man page for hwclock

man hwclock

The command to set to local time is "sudo hwclock --localtime"

---

### Post by crasher35 on 2008-12-21
Thank you so much!

---

### Post by rmjohnson144 on 2008-12-22
oops, I forgot to post my solution I got from the fellas at DFI.

> 
Ubuntu is set to use UTC time, open a terminal,

sudo <favorite editor> /etc/default/rcS

change the line UTC=yes to UTC=no

-=Mark=-

---

### Post by drjoene on 2009-02-18
Hi,

Thank you for posting this! Setting UTC=no in /etc/default/rcS worked also for me!

Greetings :)

---

### Post by zanic on 2009-08-19
[1] "sudo hwclock --localtime"
and
[2] "sudo gedit /etc/default/rcS"
change the line UTC=yes to UTC=no

didn't work for me , and i also tried 

[3] "sudo hwclock --hctosys" [set the system time from the hardware clock]

but every time i reset the comp the time still changes . I'm using Ubuntu 9.04

---

### Post by SuaSwe on 2009-08-19
As this thread is marked as solved you might want to post a new one, as people may not watch it as much! Also, include details about whether you're dual-booting, how the time changes, etc. :)

---

