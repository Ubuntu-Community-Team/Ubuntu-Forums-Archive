---
title: "Hardware RAID problems: SDA errors"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by asc99c on 2007-08-14
I am currently trying to get Ubuntu running on a PC with two hardware RAID card - one Highpoint RocketRaid RR2220, and one XFX Revo64 (which looks like a standard IDE hard disc to the system).  The actual system hard disc is a normal PATA IDE hard disc.

During the startup process, I get a sequence of error messages such as 'Buffer I/O Error on device sda1', referencing various logical blocks etc.  These errors cycle round for 10 minutes, after which it seems to time out, give up (ldm_validate_partition_table() fails), and then boot normally.

Once it is up and running, it works fairly normally.  I don't have any drivers yet working for the Highpoint card, but the Revo64 is recognised as a 1.6TB drive at /dev/sda1, mounted at /mnt/Revo0.  Contents are fully readable, over the network to Windows PCs.

During the install process (and the CD recovery option) this 10 minute timeout seems to be restarted at each step - i.e. detecting hardware, wait 10 minutes, enter hostname, wait 10 minutes ...  This is quite annoying as I've broken the system twice now trying to compile and install the Highpoint RAID drivers - each time, it takes about 3 hours to startup the recovery option.

Is it possible to disable the checking of the sda devices during initial boot-up? (as mentioned, the system disc is PATA - /dev/hda1)

NB I'm fairly new to Linux, so if there's particular information required to narrow down the problems let me know.

---

