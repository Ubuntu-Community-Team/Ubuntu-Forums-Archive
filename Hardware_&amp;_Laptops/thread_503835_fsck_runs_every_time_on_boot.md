---
title: "fsck runs every time on boot"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by ittiam on 2007-07-18
From the time I upgraded to feisty from edgy I am having this problem. fsck is run on all the windows drive every time i boot. And fsck one of the drive fails because it is a FAT 16 formatted drive. The error it says is that it does not match the backup and dumps sequence of number which i guess is sector numbers or something. But it continues to boot properly after that. I have a dell laptop who had already preconfigured a small partition as FAT 16 and that is 0th sector. I cant even delete that partition. 

Also every time i boot into linux sometimes i hear the hard disk making some noise particularly when I am installing something and when it boots up. I am afraid of this because when i first updated to feisty from edgy I had all these problems but i continued working on it and after a week or so my hard disk had a mechanical failure ..like it would make continuous tick sounds on boot and eventually I had to get a new one.  I absolutely have no idea why this failure occurred out of the blue. But I did notice hard disk making some "grrrrr" noise after I upgraded to fesity before it bombed. 

So can any one let me know why am I getting this sound even with the new hard disk or is there a problem with fsck happening every time on reboot and then throwing an error like i mentioned?

---

### Post by ittiam on 2007-07-18
Am i on the wrong topic posting this thread or should i go to other? I mean should this be in hardware and laptops or under some other topic?

There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00, 430:4e/52, 431:54/65, 432:4c/6d, 433:44/6f, 434:52/76, 435:20/65
  , 436:69/20, 437:73/64, 438:20/69, 439:6d/73, 440:69/6b, 442:73/20
  , 443:69/6f, 444:6e/72, 445:67/20, 446:ff/6f, 447:0d/74, 448:0a/68
  , 449:44/65, 450:69/72, 451:73/20, 452:6b/6d, 453:20/65, 454:65/64
  , 455:72/69, 456:72/61, 457:6f/2e, 458:72/ff, 459:ff/0d, 460:0d/0a
  , 461:0a/44, 462:50/69, 463:72/73, 464:65/6b, 465:73/20, 466:73/65
  , 467:20/72, 468:61/72, 469:6e/6f, 470:79/72, 471:20/ff, 472:6b/0d
  , 473:65/0a, 474:79/50, 475:20/72, 476:74/65, 477:6f/73, 478:20/73
  , 479:72/20, 480:65/61, 481:73/6e, 482:74/79, 483:61/20, 484:72/6b
  , 485:74/65, 486:0d/79, 487:0a/20, 488:00/74, 489:00/6f, 490:00/20
  , 491:00/72, 492:00/65, 493:00/73, 494:00/74, 495:00/61, 496:00/72
  , 497:00/74, 498:00/0d, 499:00/0a, 506:bf/cb, 507:cc/d8
1) Copy original to backup
2) Copy backup to original
3) No action

This is what i get when i run fsck.

I donno what option to proceed.

Can anyone suggest what am i supposed to do?

---

