---
title: "Internal HDD stops and launches spinning randomly"
date: 2012-07-24
forum: Hardware
---

### Post by qjmann on 2012-07-24
HDD in my desktop PC **stops spinning randomly** - every few minutes. OS - **Ubuntu 12**. This not causes total system hang, but when I perform any action, it waits until HDD will "wake up", usually about 30 seconds or more. I can hear how it stops and starts spinning. Looks like some power saving mode in laptops, but very long delay until HDD decides to start working again.
Possibly, **issue appeared after last system updates** - a few days ago HDD worked ok.

---

### Post by qjmann on 2012-07-24
I tried this command:
```
sudo /sbin/hdparm -S0 /dev/sda
```
... but this not helps. Issue stills the same:
Every few minutes my HDD causes some launched application to hang for a couple of seconds. After that it **spins up and then click**, at that point application unfreezes.

It looks like this HDD is ready to die. 6 bad clusters. Maybe bad clusters causes this issue with spinning down.

---

### Post by ahallubuntu on 2012-07-24
Yes, sounds like a bad hard drive.  Time to replace it.  Hard drives fail all the time.

---

### Post by americanman28 on 2012-07-24
you may have a GREEN DRIVE aka power saving

---

### Post by qjmann on 2012-07-25
> **americanman28 said:**
> you may have a GREEN DRIVE aka power saving

Tried to disable power-saving spin-down via hdparm, no effect. Installed Ubuntu onto new HDD, no problems yet. Old HDD is almost dead, I think.

---

