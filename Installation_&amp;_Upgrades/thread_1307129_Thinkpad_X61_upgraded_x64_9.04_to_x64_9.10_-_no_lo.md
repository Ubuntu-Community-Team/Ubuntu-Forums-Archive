---
title: "Thinkpad X61 upgraded x64 9.04 to x64 9.10 - no login screen"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by sforces on 2009-10-30
Running on an Thinkpad X61 laptop. Was running x64 9.04 and upgraded to x64 9.10. Upgrade process went through without issues. But now I never get a login screen. Can't seem to solve this.

[SOLVED 01-04-2010 Update]: After struggling with the upgrade a couple of days without any solution, I ended up restoring a backup that had x64 9.04. Then in end of November I tried to do another upgrade from 9.04 x64 to 9.10 x64 directly and it worked like a charm. Whatever the issues were must have been corrected with one of the updates introduced after the original 9.10 x64 release date. I've been running it ever since without major issues. My only annoyance currently deals with docking/undocking which affects the gnome theme (see this posting here: [http://ubuntuforums.org/showthread.php?t=1366415](http://ubuntuforums.org/showthread.php?t=1366415))

---

### Post by sforces on 2009-10-31
Booted on 9.10 x64 live cd. No issues running that. Did a clean install from that. Same result as when upgrade. Boots up to a black screen! Never prompts to login.](*,)](*,)](*,)

---

### Post by sforces on 2009-11-01
bump

---

### Post by fizyxnrd on 2009-11-02
Same issue, on an AMD X2 desktop.  I can boot up in recovery mode, but starting the X-server goes to a black screen and hangs.

---

### Post by javorulz on 2009-11-02
I got a similar problem, Starting Larmic with kernel 2.3.31 makes my lap reboot, trying another kernel i can log in but everything is dead, no mouse, no sound, everything is too slow

---

### Post by fizyxnrd on 2009-11-02
Reinstalling the fglrx drivers using aptitude in recovery mode fixed my issue.  Don't think that will help any sound issues, sorry.

---

