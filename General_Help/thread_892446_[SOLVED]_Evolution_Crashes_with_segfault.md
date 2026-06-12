---
title: "[SOLVED] Evolution Crashes with segfault"
date: 2008-08-17
forum: General Help
---

### Post by mgmiller on 2008-08-17
I am running Hardy (8.04.1) 32 bit with nvidia drivers from standard repos.  
kernel 2.6.24-19 generic

If I try to do anything with evolution that requires the calender, Evolution will crash.  
This includes clicking the Calendars,Memos or Tasks buttons.  Even Edit Preferences will crash.

The mail and contacts buttons are the only parts that work.

The log files say evolution-alarm has caused a segfault.  

```
Aug 17 06:38:37 tux kernel: [34371.975594] evolution-alarm[7621]: segfault at 00000000 eip b6b58283 esp bfd3c9fc error 4
```

If I click on the date and time in the top panel, the panels crash and then restart.  The log files say gnome-panel has caused a segfault (but I believe since it is trying to read the calendar info, that's the real problem here)

Things I have tried:
Renamed ~.evolution as .evolution.old and on evolution restart, a new .evolution is created....same problem.

Reinstalled Open office and evolution....same problem

created a new user and tried running evolution logged in as the new user and evolution will not run at all.  Clicking the date time in the top panel causes the panels to crash and restart.

restarted in older kernel 2.6.24-18 generic....same problem

reinstalled 2.6.24-19 generic and all modules....same problem.

Any help would be appreciated.

---

### Post by mgmiller on 2008-08-17
OK, here's an update.  After uninstalling and reinstalling Evolution and everything associated with it, I can no longer use evolution at all.  It segfaults on startup.  It now behaves the way an attempt at creating a new user did.

I can't do anything with my e-mails at all now about 5 Gig worth.

can anyone help?

---

### Post by mgmiller on 2008-08-20
As it turns out, I was able to help myself.  This is interesting.

Evolution can segfault if the timezone data is missing or corrupt.  Another clue is clicking on the date time applet in the top panel causes the panels to crash and restart.

reinstall the following packages:
gnome-system-tools
tzdata

This last package contains /usr/share/zoneinfo.tab  which is very important.  Without it, you can't set the time zone and will crash the date-time applet if you try to set the time zone.  

Once I had reinstalled those 2 packages, evolution and the date time applet in the top panel started working again.

Why did all this happen?

It happened because my power supply was failing. At first there was a period of time where my system would just freeze and become so unresponsive that the only thing I could do was toggle the power switch.  Later, it would just shut the machine down without warning.  It also probably is what cooked my hard drive which kept getting many errors requiring automatic file system fixes (fsck) on reboot, but finally got so bad it refused to boot at all.

A new power supply and hard drive with ghost4linux to "transfer from a bad old drive to a good new drive" (yes, that option actually exits in the the program) got me up and running again, but with the problems noted above.


Hope someone else finds this useful.

---

