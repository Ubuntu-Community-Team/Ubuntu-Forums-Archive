---
title: "Toss Hard drive?"
date: 2015-08-01
forum: Hardware
---

### Post by ncage on 2015-08-01
Hey guys, i've had a hard drive acting up for probably umm 4 months. Its a WD 750GB 7200rpm drive. When i first noticed it i was using windows. It got so bad that when i was downloading something on my cable internet and redirected it to that drive that it would saturate the drive and the drive would stay lit constantly and it would lock up the browser. I've tried a variety of things:

1. Ran spinrite on the drive. Right now spinrite is buggy and the dreaded "division overflow error" would appear. It did get through about 70% of the drive though before it failed with the error without reporting any drive errors.
2. Ran stablebit scanner on the drive (which also scans smart for problems) and it found nothing
3. I just reformated the drive with ext4 an ran badblocks on it (which is part of the formatting process). I think it tries to do 4 passes well two passes on the drive took ~150 hours. I ended up killing it after that because i needed to reboot the machine.

Whats wierd i've never had any errors reported from the drive its just slower than snot. 

Today i tried to copy a 4GB file from a faster drive in the machine. Everything looked fine until ~1.3gb. The copy processes then halted for ~30sec. It then picked back up at around paltry 5.3 MB/sec. I've never had a drive like this that just slowed down and didn't show any errors. Would you guys just dump the drive.

---

### Post by ncage on 2015-08-01
[ATTACH=CONFIG]263576[/ATTACH][ATTACH=CONFIG]263577[/ATTACH]

---

### Post by Bashing-om on 2015-08-01
ncage; Hello;

To soon to make that call.
What does a SMART test reveal ?
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
Maybe look at it from 'testdisk's' view point:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Then depending I might wind up zero'n out that hard drive with the 'dd' tool and put that drive back in service as a data disk .

[INDENT][INDENT]maybe YES
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tgalati4 on 2015-08-02
Could be a cable problem, or a SATA controller problem, or the driver controller electronics are heating up causing the slow down.  The drive head and media are probably OK.  Put the drive in another machine with a new cable and see what it does.

---

