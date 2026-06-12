---
title: "Can't burn DVD disks"
date: 2008-11-05
forum: Hardware
---

### Post by dentaku65 on 2008-11-05
Since I switch to Intrepid I'm not able to burn DVD; I've queued my issue il launchpad... anyone else have this problem?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275859](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275859)

---

### Post by dentaku65 on 2008-11-05
bump!

Anyway, I had this weird thing, I insert a blank dvd+rw, then I burn an ISO by command line, this is the output:
```
growisofs -dvd-compat -Z /dev/scd0=/home/sava/Desktop/opengeu-8.04.1-desktop-i386.iso
Executing 'builtin_dd if=/home/sava/Desktop/opengeu-8.04.1-desktop-i386.iso of=/dev/scd0 obs=32k seek=0'
/dev/scd0: pre-formatting blank DVD+RW...
/dev/scd0: "Current Write Speed" is 4.1x1352KBps.
    4489216/726503424 ( 0.6%) @1.0x, remaining 10:43 RBU 100.0% UBU   4.8%
   15892480/726503424 ( 2.2%) @2.5x, remaining 5:12 RBU 100.0% UBU  76.2%
   27197440/726503424 ( 3.7%) @2.4x, remaining 4:17 RBU 100.0% UBU  76.2%
   38600704/726503424 ( 5.3%) @2.5x, remaining 4:09 RBU 100.0% UBU  76.2%
   49905664/726503424 ( 6.9%) @2.4x, remaining 3:50 RBU 100.0% UBU  76.2%
   61308928/726503424 ( 8.4%) @2.5x, remaining 3:36 RBU 100.0% UBU  76.2%
   72712192/726503424 (10.0%) @2.5x, remaining 3:35 RBU 100.0% UBU  76.2%
   84017152/726503424 (11.6%) @2.4x, remaining 3:26 RBU 100.0% UBU  76.2%
   95420416/726503424 (13.1%) @2.5x, remaining 3:18 RBU 100.0% UBU  76.2%
  106823680/726503424 (14.7%) @2.5x, remaining 3:17 RBU 100.0% UBU  76.2%
  118095872/726503424 (16.3%) @2.4x, remaining 3:10 RBU 100.0% UBU  76.2%
  129433600/726503424 (17.8%) @2.5x, remaining 3:04 RBU 100.0% UBU  76.2%
  140836864/726503424 (19.4%) @2.5x, remaining 3:02 RBU 100.0% UBU  76.2%
  152141824/726503424 (20.9%) @2.4x, remaining 2:57 RBU 100.0% UBU  76.2%
  163446784/726503424 (22.5%) @2.4x, remaining 2:52 RBU 100.0% UBU  76.2%
  174850048/726503424 (24.1%) @2.5x, remaining 2:50 RBU 100.0% UBU  76.2%
  186318848/726503424 (25.6%) @2.5x, remaining 2:45 RBU 100.0% UBU  76.2%
  197591040/726503424 (27.2%) @2.4x, remaining 2:43 RBU 100.0% UBU  76.2%
  208961536/726503424 (28.8%) @2.5x, remaining 2:38 RBU 100.0% UBU  76.2%
  220364800/726503424 (30.3%) @2.5x, remaining 2:33 RBU 100.0% UBU  76.2%
  231768064/726503424 (31.9%) @2.5x, remaining 2:31 RBU 100.0% UBU  76.2%
  243073024/726503424 (33.5%) @2.4x, remaining 2:27 RBU 100.0% UBU  76.2%
  254476288/726503424 (35.0%) @2.5x, remaining 2:22 RBU 100.0% UBU  76.2%
  265879552/726503424 (36.6%) @2.5x, remaining 2:20 RBU 100.0% UBU  76.2%
  277282816/726503424 (38.2%) @2.5x, remaining 2:16 RBU 100.0% UBU  76.2%
  288587776/726503424 (39.7%) @2.4x, remaining 2:12 RBU 100.0% UBU  76.2%
  299991040/726503424 (41.3%) @2.5x, remaining 2:09 RBU 100.0% UBU  76.2%
  311394304/726503424 (42.9%) @2.5x, remaining 2:05 RBU 100.0% UBU  76.2%
  322797568/726503424 (44.4%) @2.5x, remaining 2:01 RBU 100.0% UBU  76.2%
  334200832/726503424 (46.0%) @2.5x, remaining 1:58 RBU 100.0% UBU  76.2%
  345505792/726503424 (47.6%) @2.4x, remaining 1:54 RBU 100.0% UBU  76.2%
  357007360/726503424 (49.1%) @2.5x, remaining 1:50 RBU 100.0% UBU  76.2%
  368410624/726503424 (50.7%) @2.5x, remaining 1:47 RBU  99.9% UBU  76.2%
  379715584/726503424 (52.3%) @2.4x, remaining 1:44 RBU  99.7% UBU  76.2%
  391053312/726503424 (53.8%) @2.5x, remaining 1:40 RBU  99.9% UBU  76.2%
  402522112/726503424 (55.4%) @2.5x, remaining 1:37 RBU  99.9% UBU  76.2%
  413892608/726503424 (57.0%) @2.5x, remaining 1:33 RBU 100.0% UBU  76.2%
  425164800/726503424 (58.5%) @2.4x, remaining 1:30 RBU  99.9% UBU  76.2%
  436535296/726503424 (60.1%) @2.5x, remaining 1:27 RBU 100.0% UBU  76.2%
  447938560/726503424 (61.7%) @2.5x, remaining 1:23 RBU 100.0% UBU  76.2%
  459341824/726503424 (63.2%) @2.5x, remaining 1:19 RBU 100.0% UBU  76.2%
  470843392/726503424 (64.8%) @2.5x, remaining 1:16 RBU 100.0% UBU  76.2%
  482148352/726503424 (66.4%) @2.4x, remaining 1:12 RBU 100.0% UBU  76.2%
  493453312/726503424 (67.9%) @2.4x, remaining 1:09 RBU 100.0% UBU  76.2%
  504856576/726503424 (69.5%) @2.5x, remaining 1:06 RBU 100.0% UBU  76.2%
  516259840/726503424 (71.1%) @2.5x, remaining 1:02 RBU 100.0% UBU  76.2%
  517537792/726503424 (71.2%) @0.3x, remaining 1:03 RBU 100.0% UBU 100.0%
  529629184/726503424 (72.9%) @2.6x, remaining 0:59 RBU 100.0% UBU  76.2%
  548700160/726503424 (75.5%) @4.1x, remaining 0:53 RBU 100.0% UBU  76.2%
  567672832/726503424 (78.1%) @4.1x, remaining 0:46 RBU 100.0% UBU  76.2%
  586678272/726503424 (80.8%) @4.1x, remaining 0:40 RBU 100.0% UBU  76.2%
  605650944/726503424 (83.4%) @4.1x, remaining 0:34 RBU 100.0% UBU  76.2%
  624689152/726503424 (86.0%) @4.1x, remaining 0:28 RBU 100.0% UBU  76.2%
  643661824/726503424 (88.6%) @4.1x, remaining 0:23 RBU  99.9% UBU  76.2%
  662634496/726503424 (91.2%) @4.1x, remaining 0:17 RBU 100.0% UBU  76.2%
  681607168/726503424 (93.8%) @4.1x, remaining 0:12 RBU 100.0% UBU  76.2%
  700579840/726503424 (96.4%) @4.1x, remaining 0:07 RBU  77.3% UBU  76.2%
  719552512/726503424 (99.0%) @4.1x, remaining 0:01 RBU  20.8% UBU  76.2%
builtin_dd: 354752*2KB out @ average 2.7x1352KBps
/dev/scd0: flushing cache
/dev/scd0: writing lead-out

```
Eject the dvd, reinsert... tak, the dvd+rw is still blank!](*,)

---

### Post by anamorgan on 2008-11-05
I used to get this problem beofre, might be because of wirus or that my motehrboard is aged long. What ever, reinstall xp and this solves teh problem. Trust me.

---

### Post by nixxofugi on 2008-11-19
any luck with this??? need to burn a dvd soon and i am having tons of problems here... please help :-)

---

### Post by Yezinki on 2008-11-20
Clean optical drive lens & use good burning media!

---

