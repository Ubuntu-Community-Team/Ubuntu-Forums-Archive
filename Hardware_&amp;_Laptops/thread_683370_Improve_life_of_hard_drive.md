---
title: "Improve life of hard drive"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by s1m0n13 on 2008-01-30
I've come across a number of posts about how running the latest version of Ubuntu Gutsy Gibbon on a laptop could possibly end up in a shorter life for your laptop hard disk. 

The recommended fix is to use hdparm; a command line tool to disable advanced power management (APM). The recommended command is below:
$ sudo hdparm -B 255 /dev/sda

Has anyone experimented with this?  What are the pros & cons of performing this action?

---

### Post by kegobeer on 2008-01-30
Honestly, I take little notice of any article or post that says running a particular operating system will shorten the life of my drive.  If an operating system can shorten the life, then programs that constantly access the driver will also shorten the life.

Don't waste your time worrying about this.

---

### Post by Whiffle on 2008-01-30
Actually it IS worth worrying about.  Read up on the issue.

I run that command on mine, it stops it from unloading/loading the head all the time.  I havn't noticed any performance decreases.

---

### Post by s1m0n13 on 2008-01-31
Here's a link to the launchpad discussion...
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

Has anyone run into any issues w/ your hard drive heating up after disabling apm?  It seems to be the only negative w/ running the command.

---

