---
title: "Samsung YP-S3 mounting / file transfer under MTP"
date: 2009-11-15
forum: Hardware
---

### Post by zombietris on 2009-11-15
I've just ordered a Sammy YP-S3 and I realise that it won't mount on EU firmware on anything other than MTP.

I've been poking around on the forums (longtime lurker, 1st time poster) and found this way of mounting MTP under ubuntu [http://ubuntuforums.org/showthread.php?t=848495](http://ubuntuforums.org/showthread.php?t=848495)

I've confirmed the above works with my Sansa Fuze which had gotten itself stuck in MTP mode (long tedious story), I'm just wondering if there's any reason why I can't transfer over the korean firmware & config.dat file (with UMS/  MSC support) when it's force mounted in this fashion? I'm essentially trying to replicate the process described halfway down this page  [http://www.overclock.net/other-software/433762-samsung-s3-wont-play-ogg.html](http://www.overclock.net/other-software/433762-samsung-s3-wont-play-ogg.html) but without an XP machine.

Hopefully it'll be here soon to try myself but I'm just wondering if anyone's had sucess transferring non music files when mounted in this way?

Cheers and if all else fails I'll report back on whether this works when I try it.

---

### Post by zombietris on 2009-11-20
Okay, anyone who's interested, the results.

You can force mount the S3 under Ubuntu Karmic & you can transfer the Korean firmware over to it but for some strange (& annoying) reason you can't use gedit to generate the config.dat file as  all that happens is you update to the EU version of the firmware .rom you put on the drive.

I generated the config.dat on my windows pc at work & emailed it to home (restricted usb access meant I coudn't upgrade it @ work), dragged the s3.rom file & the config.dat onto the force mounted S3, unplugged it and bingo bango bongo, 1 yp-s3 in MSC mode complete with ID3 tag compliance (which force mounting doesn't give you as it doesn't update the database)

So there we go, barring a config.dat file you can do the whole process in Ubuntu and if you've got a mate with a Windows PC they can email you that so you don't even have to get out of your seat! :P

---

