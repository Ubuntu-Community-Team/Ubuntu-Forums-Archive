---
title: "Turn off disk utility notification"
date: 2011-06-01
forum: Hardware
---

### Post by wildmanne39 on 2011-06-01
Hi, I have in external usb drive that has ten bad blocks on it and disk utility keeps giving notifications about it every few seconds, is there a way to turn that notification off? Thank you for your help I really appreciate it.

---

### Post by elliotbeken on 2011-11-08
i have the exact problem with one of my Ubuntu server !

if i leave the server and come back to it a few hours later i will have over a hundered notifications open 

anyone have any ideas

---

### Post by BillyBoa on 2011-11-08
I don't know if you chkdsk from Windows is solving the problem. Maybe you could use the drive as external and chkdsk sometimes, takes long to do it.

---

### Post by IcarusR on 2011-11-08
> I don't know if you chkdsk from Windows is solving the problem. Maybe you could use the drive as external and chkdsk sometimes, takes long to do it.

Depends on filesystem, chkdsk will only work on windows fs & not work on linux fs.

---

### Post by BillyBoa on 2011-11-08
> **IcarusR said:**
> Depends on filesystem, chkdsk will only work on windows fs & not work on linux fs.
Yes you have right. I tried to chkdsk a ext4 drive but it's impossible. In that case the silly solution should be to backup the system, format the drive to NTFS and detect and mark the bad sectors.

---

