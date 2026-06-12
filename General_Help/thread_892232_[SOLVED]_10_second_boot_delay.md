---
title: "[SOLVED] 10 second boot delay"
date: 2008-08-16
forum: General Help
---

### Post by BeachBum on 2008-08-16
Hello everyone,

I've been hellbent on improving my startup time recently, since I use a laptop for class.  I'm almost always late, and having to wait 60s or so for a working desktop is a nuisance.  Ironically enough, shutdown time is on the order of 20s, however boot up time is on the order of a minute.  I've followed several guides for readahead, using sysv-rc-conf, BUM, and a few others.  I found out about bootchart and the first thing I've noticed is a delay where nothing is happening from 0s to 10s that I haven't seen on other bootcharts floating around the web.  Anyone have any suggestions on shortening this up?

Thanks!

---

### Post by fsmithred on 2008-08-19
Look in your BIOS for a boot delay setting. If you make the time too short, you may run into a problem with trying to boot before the disk spins up.

---

### Post by BeachBum on 2008-09-19
Unfortunately this is a laptop bios so options are scarce.  I've tweaked a few things and gotten the boot time down a few seconds.  Still have a 10s delay where nothing happens.  Anyone have any tips?

Thanks!

---

### Post by llebegue on 2008-09-19
I can see cupsys in your boot chart.
If you do not intent to use a printer you can try to avoid starting this service.

Edit :
ditto with virtualbox if you don't use it in your classroom.

Edit again :
I saw you removed cupsys in your second post ;-)

---

### Post by -Zeus- on 2008-09-19
so..... you're sure that's not the timeout in your menu.lst, right?

---

### Post by BeachBum on 2008-09-19
I checked and there was a 10s delay in my menu.lst, which I changed to 2 and the bootchart still looks the same.

dmesg doesn't show any errors but does confirm there is no activity.  Logs are attached.

Also, I use virtualbox regularly for office 2007 (my school likes to distribute material electronically, and office 07 works much more smoothly than OO.org on these large complicated documents) so uninstalling is not the best option.

---

### Post by BeachBum on 2008-11-04
After an upgrade to Ibex, I noticed a new error in dmesg which pointed to the 10s culprit: EHCI: BIOS handoff failed (BIOS bug ?)

A quick google search revealed that if I turn off legacy USB support in my bios, everthing would be peachy.

Attached are the before and after bootcharts of a fresh Ibex install, with only profile done at a previous boot.  From this simple tweak, I gained 9s!  Wheee!

---

