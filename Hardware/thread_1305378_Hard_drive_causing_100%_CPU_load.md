---
title: "Hard drive causing 100% CPU load"
date: 2009-10-29
forum: Hardware
---

### Post by Chonnawonga on 2009-10-29
I recently set up a new hard drive, and whenever I'm doing anything with any amount of hard drive activity (ex. Firefox, Transmission) it ramps up my CPU usage to 100%. (This CPU load doesn't show up in gnome-system-monitor, but it does on the gnome-do docky CPU monitor and it causes a rather frustrating slowdown of the system.)

The drive is a 1.5 TB Western Digital "Green" hard drive in a NexStar CX enclosure on an eSATA connection. The drive is mounted as /home/user. Running another user with a different /home partition resolves the issue.

Can anyone tell me what the connection is between the hard drive and the CPU load? What can I do to use the drive for my /home/user partition without getting the slowdowns?

---

### Post by perky on 2009-11-23
I'm getting the same, with the same configuration.

Moving data via eSATA goes at a painfully slow 3.1mb/sec (to an ext4 partition on the external 1.5tb).  I think the CPU might be wrongly limiting the transfer speed?

CPU is a 2.67ghz

Haven't tested the different locations/permissions/users.

---

### Post by perky on 2009-11-23
Update:  some transfers go at normal speed (~44mb/sec).  All transfers have been from home directory, so should have same permissions/user.

Does anyone know how to get full transfer speeds for everything?

---

### Post by Chonnawonga on 2009-12-12
Perky,

Have you tried going to a regular SATA connection (rather than eSATA) and seeing if that makes a difference?

---

### Post by Chonnawonga on 2010-07-09
If anyone trips across this, the answer is here: [http://www.linuxconfig.org/linux-wd-ears-advanced-format]("http://www.linuxconfig.org/linux-wd-ears-advanced-format")

---

