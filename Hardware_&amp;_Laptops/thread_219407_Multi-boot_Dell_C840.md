---
title: "Multi-boot Dell C840"
date: 2006-07-19
forum: Hardware &amp; Laptops
---

### Post by ipatt on 2006-07-19
I multi-boot to Win2000, WinXP or DOD 7.10 on a Dell C840 using Terabyte Unlimited's BootIT NG.
 When my Dapper Dan (v6.06) CD arrived I promptly put in the drive and rebooted for a live configuration. Dapper Dan tried to boot but seemed to get hung looking for hdb. There is only one HDD on this machine. Finally, there were errors generated (don't remember the module) and I had to manually shut down the machine.
 Worse, WinXP would boot only with difficulty (long time, much disk access). I did a restore and and a reboot to the last known good configuration. This helped. I then booted to Win2000 and chkdsk complained of many (index) errors on the partition containing WinXP. It fixed them and finally I got my WinXP back.
 A note: BootIt works by creating an "extended" MBR with the partition and boot info particular to the OS chosen at boot time.
 2nd note: Ubuntu v5.10 did not cause any of these problems using the live CD.

 Any ideas anyone??

---

