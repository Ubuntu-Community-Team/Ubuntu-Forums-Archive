---
title: "Ext3 file - folder problem"
date: 2008-11-02
forum: General Help
---

### Post by ivanpaparaka on 2008-11-02
Hi,

I was messing with one of my HDDs, because it would become read only because of some error it can't fix:
```
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  430:4e/52, 431:54/65, 432:4c/6d, 433:44/6f, 434:52/76, 435:20/65, 436:69/20
  , 437:73/64, 438:20/69, 439:6d/73, 440:69/6b, 442:73/20, 443:69/6f
  , 444:6e/72, 445:67/20, 446:ff/6f, 447:0d/74, 448:0a/68, 449:44/65
  , 450:69/72, 451:73/20, 452:6b/6d, 453:20/65, 454:65/64, 455:72/69
  , 456:72/61, 457:6f/2e, 458:72/ff, 459:ff/0d, 460:0d/0a, 461:0a/44
  , 462:50/69, 463:72/73, 464:65/6b, 465:73/20, 466:73/65, 467:20/72
  , 468:61/72, 469:6e/6f, 470:79/72, 471:20/ff, 472:6b/0d, 473:65/0a
  , 474:79/50, 475:20/72, 476:74/65, 477:6f/73, 478:20/73, 479:72/20
  , 480:65/61, 481:73/6e, 482:74/79, 483:61/20, 484:72/6b, 485:74/65
  , 486:0d/79, 487:0a/20, 488:00/74, 489:00/6f, 490:00/20, 491:00/72
  , 492:00/65, 493:00/73, 494:00/74, 495:00/61, 496:00/72, 497:00/74
  , 498:00/0d, 499:00/0a, 506:bf/cb, 507:cc/d8
1) Copy original to backup
2) Copy backup to original
3) No action
? 2 
Leaving file system unchanged.
/dev/sdc1: 95443 files, 1095961/1279551 clusters

```
I tried editing /etc/fstab and after a few mount/umounts, a folder called DOWNLOADS, has turned into an "Unknown file" ?DOWNLAODS. 
If I try to view it, I get "not a rgular file" error.
I tried fsck, but it gave me the same output as above.
Here is fstab before and after:
```
# /dev/sdc1
UUID=320640c7-52d4-463e-ad7c-eecd23aeb93e /media/rack1    ext3    relatime        0       2

```
After the error I returned it to it's default (the above one)
```
# /dev/sdc1
UUID=320640c7-52d4-463e-ad7c-eecd23aeb93e /media/rack1    ext3    relatime,user,rw,sync,auto        0       2

```

How can I transform it back a dir?

---

