---
title: "dvd drive issues"
date: 2012-09-14
forum: Hardware
---

### Post by acefromspace on 2012-09-14
I got a used dvd drive (optiarc dvd rw ad-7220A) and it seemed to work OK, so I burned a bunch of data and also some iso images. K3b showed successful burns. Everything seemed to be working, so I deleted some important files I believed to be backed up (was very low on hard drive space) Now, the drive is acting up: won't read dvds I burned, and when I press eject button on drive, it opens and immediately recloses (I have a disc in right now... it won't let me get it out) also, the dvd with iso image burned won't play in home dvd player (used devede to create iso... never had problems before) I really messed up relying on this drive for backups... many files may be lost! I've read many threads about issues, especially with optiarc drives. I'm using ubuntu 10.04 from fresh install. Is this a firmware issue, or are these drives just a piece of sh*t? The drive looks clean, but I will open it and make sure ( just now finally got disk out... it kept trying to read it and wouldn't give up for long time) I'm quickly losing faith in optical drives. Is there a chance another drive can read these dvds? By the way, it will read sometimes... very erratic. I do have ubuntu 9.04 on another hard drive... might try it in case this is a 10.04 issue ( I hope not because I am otherwise happy with 10.04 )

---

### Post by Epodx64 on 2012-09-15
Sounds like the drive is failing do you have access to another DVD-Rom drive that you might be able to pull your data from? I had a dvd-rw drive fail me and made some backup's before hand and was still able to pull the data off with a different drive. 

I'd say optical media is about dead I really don't use it for anything anymore my dvd-rw drive I pulled from a Dell Dimension 4700 it's starting to show it's age that's for sure seems slow somehow but I rarely use it anymore I use Usb pendrives for all my installations now I have a Pendrive with just my important backups and I have a separate 70Gb ext3 partition on my second sata drive unmounted that I back everything up to I wouldn't be surprised too see the old' dvd-rom drive go the way of the floppy soon. blu-ray may prolong it's life some i'd imagine but even if I had a blu-ray drive i'd still use Usb pendrives.

---

### Post by acefromspace on 2012-09-16
Opened up drive... very clean except spindle, so I cleaned it and did some tests. Data CD, music CD, data DVD, and movie DVD all play. Going to try burning data DVD, this time with verify data. I think I know why I had trouble: hard drive was so full there wasn't enough space in Temp folder (duh!) Also, I noticed K3b defaults to 4Mb buffer... my drive specs say 2Mb (don't know if that matters) Will post results of burn.

---

### Post by acefromspace on 2012-09-16
Good news! Burn success, including verify data. Drive reads dvd fine. Also burned iso image... success. Will test in home dvd player. It is a very noisy drive! Didn't expect it to work. Too bad I made all those "coasters" before (and lost many files) I left the burn speed on auto... some of the others I had tried slower speeds (not sure if that was an issue) Maybe just needed the spindle cleaned?

---

### Post by acefromspace on 2012-09-16
Burned iso image, works in home dvd player.
I would mark this a solved, but I don't know for sure what caused the problems.
It had nothing to do with ubuntu 10.04 and I am looking forward to trying the newest LTS version. I don't understand why K3b allowed and completed "successful" burn if temp folder didn't have enough space. I should have noticed, but I would expect it would bring up warning. The main reason I got this drive was to burn iso images, and I'm getting a larger hard drive, so I won't rely on this drive for critical backup. The files I lost were just low quality videos, so no big deal, but I should have used verify data the very first burn!

---

