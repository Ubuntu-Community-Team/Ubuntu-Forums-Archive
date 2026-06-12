---
title: "Random Lock Out"
date: 2009-08-10
forum: Hardware
---

### Post by fleamour on 2009-08-10
Xubuntu seems to run fine on my IBM T21 for the most part.  However it crashes fairly regularly where it'll lock up with both the num lock & caps lock lights flashing in quick succession.

Anyone else experienced this?

---

### Post by fleamour on 2009-08-11
Actually it's the scroll lock & caps lock.

Apparently it's a kernel panic.  But I cannot seem to find an exact fix.  Current kernel is 2.6.24-24.  Any help much appreciated.

EDIT:  Would running previous kernel 2.6.24-19 help?

---

### Post by fleamour on 2009-08-11
The only way to recover from the crash is Alt + SysRq + REISUB to restart computer.

---

### Post by fleamour on 2009-08-16
I have upgraded to Jaunty where I can reliably reproduce a kernel panic by trying to hibernate.  This is avoidable by not hibernating, as long as it does not randomly happen with day to day use, like Hardy, then I can live with it.  I will also try rolling back a kernel with StartUp-Manager & see what happens.

---

### Post by fleamour on 2009-08-17
After some research it would seem the kernel panic only happens after resuming from standby/hibernate (both non-functional in Jaunty.)  She'll run rock steady all day as long as you shutdown & reboot each session.

---

