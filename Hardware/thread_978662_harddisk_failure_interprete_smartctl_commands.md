---
title: "harddisk failure: interprete smartctl commands"
date: 2008-11-11
forum: Hardware
---

### Post by karlrt on 2008-11-11
Hi!

I allready posted this in the [german forum]("http://forum.ubuntuusers.de/topic/festplattenproblem:-smartctl:-current-pending/"), but i wanna post it in english to to get a broader audience to see my problem. If this is concidered double posting and against any code of conduct, pls. tell me. Right now i hope thats ok:

Here it is:

Somehow, i could not boot no more in my primary partition, luckily, i have some other (testing) partitions i could boot in. The file system is not corrupted, somehow i can read data (doing backups right now) Running smartctl gives me this output:

[http://paste.ubuntuusers.de/392812/]("http://paste.ubuntuusers.de/392812/")

line 28 is worrying me, cause the "current_pending_sector" value goes up, when i started it was by 6, in the pastebin it says 10, right now im at 21!
the selftest (short and long) too is not passing, it stops after 10 % (90% still going) with the first bad sectors showing up.

From this bad block error, i did the following howto, but it somehow didnt change much:

[http://smartmontools.sourceforge.net/BadBlockHowTo.txt]("http://smartmontools.sourceforge.net/BadBlockHowTo.txt")

i also tried this automated by script:

[http://www.pro-linux.de/t_system/badblock.html]("http://www.pro-linux.de/t_system/badblock.html") (german)

didnt give any errors, but didnt help much, the next selftests still failed!

I also posted the log of the failing system start:

[http://paste.ubuntuusers.de/392813/]("http://paste.ubuntuusers.de/392813/") 

I think interesting are only the errors here: (row 486):
```
res 41/40:00:b8:a0:99/0d:00:00:00:00/40 Emask 0x409 (media error) <F>
ata1.00: configured for UDMA/133
ata1: EH complete
[sda] 312581808 512-byte hardware sectors (160042 MB)
[sda] Write Protect is off
[sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUAe
```

these are the outputs of smartctl -l error /dev/sda it doesnt make me happy:

[http://paste.ubuntuusers.de/392817/]("http://paste.ubuntuusers.de/392817/")

does anybody know what that means? i mean the commandos?
```
  60 08 00 65 b3 76 01 08      00:25:09.307  READ FPDMA QUEUED
  27 00 00 00 00 00 00 08      00:25:09.307  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      00:25:09.306  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      00:25:09.306  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      00:25:09.280  READ NATIVE MAX ADDRESS EXT
```

I hope you can help me, and perhaps tell me i should replace the harddisk right away! Thanks in advance!

---

