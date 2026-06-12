---
title: "How-to: Ubuntu don't use badblocks"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by cardil on 2007-04-17
Hi. I've got a question. How to tell linux not to use bad sectors on my disk. I've got an old computer DELL PII 333 +128MB RAM +old 20GB hdd. I been doing this:
1. Using liveCD (old Aurox 9) I crated 2 partition with parted: 256MB ext2 (to be swap) and ~19GB ext3.
2. I run: fsck -cs /dev/hda1 /dev/hda2
It run a while. For hda1 it run quickly but in hda2 my drive was several times struck (that was bad blocks)
3. Then I install ubuntu. Formated hda1 to swap and only mouted hda2 to /(dont format or change partition)
4. But my system still hangs out . Mayby not every bad blocks was found?
this is part of /var/log/messages
```

Apr 17 12:12:13 SERWER333 kernel: [42949424.290000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 17 12:31:58 SERWER333 -- MARK --
Apr 17 12:51:59 SERWER333 -- MARK --
Apr 17 13:11:59 SERWER333 -- MARK --
Apr 17 13:32:00 SERWER333 -- MARK --
Apr 17 13:58:05 SERWER333 syslogd 1.4.1#18ubuntu6: restart.
```

Is there a way to force fsck -c without running some liveCD?!?

---

