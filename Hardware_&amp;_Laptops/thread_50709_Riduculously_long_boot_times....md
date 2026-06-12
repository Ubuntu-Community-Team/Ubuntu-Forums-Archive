---
title: "Riduculously long boot times..."
date: 2005-07-21
forum: Hardware &amp; Laptops
---

### Post by gammyhand on 2005-07-21
I am guessing this is a hardware conflict somewhere hence using this forum. Occasionally when I start ubuntu it takes a LONG time to boot up. I literally mean 10-15 minutes. Normal boot time is 30-40 seconds. Any ideas what would cause this?

---

### Post by codejunkie on 2005-07-21
[QUOTE=gammyhand]I am guessing this is a hardware conflict somewhere hence using this forum. Occasionally when I start ubuntu it takes a LONG time to boot up. I literally mean 10-15 minutes. Normal boot time is 30-40 seconds. Any ideas what would cause this?[/QUOTE]
a failing hard drive can cause this because it cant read the data, does your hard drive make a lot of noise like grinding for long periods of time when data isn't being written to it. if you dual boot has it ever taken that long to load windows or another os.

---

### Post by gammyhand on 2005-07-21
[QUOTE=codejunkie]a failing hard drive can cause this because it cant read the data, does your hard drive make a lot of noise like grinding for long periods of time when data isn't being written to it. if you dual boot has it ever taken that long to load windows or another os.[/QUOTE]
 Nope, no errors on the hard drive. It's working fine and dandy :)

---

### Post by codejunkie on 2005-07-21
[QUOTE=gammyhand]Nope, no errors on the hard drive. It's working fine and dandy :)[/QUOTE]
what does it freeze at when it does this maybe it's a module that its trying to load causing this.

---

### Post by gammyhand on 2005-07-21
Hard to tell as I use splashy....it doesn't really freeze at one place, the progress bar just slows to a complete crawl.

---

### Post by codejunkie on 2005-07-21
[QUOTE=gammyhand]Hard to tell as I use splashy....it doesn't really freeze at one place, the progress bar just slows to a complete crawl.[/QUOTE]

if this is happening often you might want to disable splashy for a while so you can diagnose the problem because 10-15 minute boot times don't sound good.

---

### Post by gammyhand on 2005-07-21
Ok, I will do that . Thanks.

---

### Post by mjkelly on 2005-07-21
did you check the logs for errors?

also, sometimes my system takes 5-10 minutes to boot if the networks down.

---

### Post by gammyhand on 2005-07-22
[QUOTE=mjkelly]did you check the logs for errors?

also, sometimes my system takes 5-10 minutes to boot if the networks down.[/QUOTE]
 Where is the log file located? Thanks.

---

### Post by luopio on 2005-08-18
logs on linux systems: 
write **dmesg** in a console-- shows the kernel messages (see **man dmesg**)

logfiles are located in /var/log. the names of the files there depend on the distribution and the logger in use. it seems that on ubuntu (5.04) you have the general logmessages in **/var/log/messages** and then, for example, the X-server messages in the various Xorg.* files (see with ls -t -l X* to find the latest one).

for your problem only the output of dmesg right after booting is needed.

---

