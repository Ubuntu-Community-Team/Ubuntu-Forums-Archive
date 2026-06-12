---
title: "Harddrive crash - so it finally happened."
date: 2013-04-15
forum: Hardware
---

### Post by Kols on 2013-04-15
Hi all!

I'm running a triple-boot computer with Win7/Lubuntu/Crunchbang on a very old, yet (up until now) sturdy laptop (HP Pavilion DV4000) made and bought around 2005/2006. The harddrive is equally old.

These last couple of days, I've experienced some pretty nasty hang-ups, freezes and "read-only filesystem" errors. Stupid as I was, I thought MAYBE this was harddrive related, but thought the most plausible explanation was software related.

I was wrong.

I'm now running BackTrack live to see if there was a possibility to recover my data. Checking the file manager, no hdd-partitions turned up. I did blkid to check for vital signs, but found none. 
I'm planning to try and connect the hdd to a USB-IDE/SATA cable, but I'll have to borrow one some other day. 

So doc, what are my options?

tl;dr : I'm stupid and didn't back up, now hdd seems dead - what do?

EDIT: I'm now actually accessing all partitions through my Lubuntu-partition, and I'm currently copying. Let's just hope this lasts long enough for me to get it all copied and backed up... 
What checks can I do to confirm this is actually a crash/hardware-error situation?

---

### Post by ahallubuntu on 2013-04-15
~

---

### Post by tgalati4 on 2013-04-15
If you look through your log files (/var/log/syslog and syslog.1) you may see clues to a hard drive failure:  read errors, write errors, drive cache errors.  The linux kernel expects perfect hardware, so when hardware is intermittent, it looks like software issues, but capturing the actual hardware fault is not done by any of the default system loggers.  The SMART status will capture 2/3's of the failure modes, but the remaining 1/3 will happen without notice.

For an old hard disk, it could simply be a sticky bearing that makes the platter slow to spin up.  If you have it booted or if you can read it, then capture as much data as you can before it seizes up completely.

Open a terminal, post the output of:

```
sudo smartctl -a /dev/sda
```

Your device may be different (sdb or sdc).

---

### Post by zrdc28 on 2013-04-16
If all or most of that fails and you still cannot get your data stick the hard drive in the freezer in a plastic bag of course and that might help you. 
I have had to do that several times before I got all of the data.

---

