---
title: "Hard Drive Woes - Learn From Me"
date: 2012-11-06
forum: Hardware
---

### Post by gerowen on 2012-11-06
I'm not posting this really looking for help, I've tried quite a bit and done some things to the drive so I'm aware that data recovery isn't really an option any more, and the drive is out of warranty so I'll just replace it. I just thought I'd share my story, get some input, and maybe point out something for other people to watch out for.

I recently finished 6 years on active duty with the Army (United States). I finished up at Fort Lewis, WA. I lived in an apartment off post with my wife and kid in Lakewood, WA. When I started my terminal leave I moved back to my home-town here in eastern Kentucky, just shy of 3,000 miles (4828 km) away. Movers took most of my large furniture; bookshelves, recliners, etc, and I sent my wife and kid home on a plane about a month before my leave started to get settled. I packed myself, a small dog, a cat, my electronics, guns (basically anything I didn't want to entrust to a 3rd party), enough clothes for a week and some emergency equipment into my Ford Explorer and drove the rest of my household goods home over the course of 4 days. When I left Lakewood, WA, my Western Digital 1 TB MyBook external hard drive functioned properly. The server was having issues with overheating because the thermal paste had worn out, but the external worked fine and contained a lot of backup data. I packed it in my laptop bag and stuck it in the back of the car with everything else. At some point in the ride, something must have happened to that hard drive because when I got home and plugged it in, the partition type was labeled as "Unknown". I put it on a shelf and figured I'd fix it once I got around to actually setting the server back up. Well my server is g2g again, and now that I've taken a serious look at the hard drive, it appears to be in pretty rough shape. 2 sectors marked as bad, failed the shortest self test Ubuntu would run, so the longer ones weren't even necessary. I've tried using testdisk to recover the partition but it keeps saying "write error" and for some reason guessed it as being NTFS when in fact it was EXT4. I figured I'd just reformat the whole drive as MBR, put a new partiton on it and try to use photorec to recover whatever data I could, but I can't even get the drive to format. The only magnetic devices I can think of other than the stereo speakers (normal, factory speakers) that it might have come close to is a bundle of 2 magnetic CB antenna bases that I had under the seat. I've already checked and the drive is no longer under warranty so I'll probably just replace it even though it's only 2-3 years old. I was under the impression that modern hard drives were shielded against small magnets like that though which is why I didn't sweat it, so my question is this.

WTF actually happened to my drive so I can avoid it in the future?

---

### Post by ahallubuntu on 2012-11-06
Two bad sectors is one more than required to make your S.M.A.R.T. test fail.  It's possible you have far more than two.

Hard drives fail all the time, not because someone put a big magnet next to them but because hard drives are unreliable.  They have both mechanical and electronic parts.

What you can do in the future to prevent data loss is to make regular backups and ASSUME your drive will fail, so when it does, you just replace it like any other failed component and copy your data back to it from the backup.  When I buy a 2TB archive drive, for example, I buy two at the same time: one is regularly synced up to the other one.

---

### Post by gerowen on 2012-11-06
I've got some 5.56mm rounds with this hard drive's name on it for tomorrow, I'm gonna take it out, shoot the hell out of it, and narrate it.  Then I'll upload the video to YouTube and get paid, mwahahahaha.

When I get the video recorded and uploaded I'll post a link here.

---

### Post by grahammechanical on 2012-11-06
The read/write heads of the drive float fractions of fractions of inches above the disks. Knocks, bumps and bashes against the drive can cause those heads to crash against the disks and so damage the surface of the disk making it impossible to read and write to.

[http://en.wikipedia.org/wiki/Hard_disk_drive]("http://en.wikipedia.org/wiki/Hard_disk_drive")

> Due to the extremely close spacing between the heads and the disk surface, HDDs are vulnerable to being damaged by a head crash&#8212;a failure of the disk in which the head scrapes across the platter surface, often grinding away the thin magnetic film and causing data loss. Head crashes can be caused by electronic failure, a sudden power failure, physical shock, contamination of the drive's internal enclosure, wear and tear, corrosion, or poorly manufactured platters and heads.

Being in the Army you must have heard the expression 'hardened bunker,' well, hard disks are not 'hardened.'

Sorry for you painful experience. A lesson for us all.

Regards.

---

### Post by hakermania on 2012-11-06
> **gerowen said:**
> Then I'll upload the video to YouTube and get paid, mwahahahaha.

When I get the video recorded and uploaded I'll post a link here.
Hah! Can't wait!

I've heard that strong magnets can seriously damage HDs. Haven't tested it myself though!

---

### Post by dannyboy79 on 2012-11-06
> **ahallubuntu said:**
> When I buy a 2TB archive drive, for example, I buy two at the same time: one is regularly synced up to the other one.I never buy 2 of the same drives at the same time due to the fact when drives are bad, they're bad in bunches. Just my 2 cents.

---

### Post by gerowen on 2012-11-06
Video is rendering right now, but here's a photo.

---

### Post by jerome1232 on 2012-11-06
I'm using this photo for "How do I securely erase my hard drive" threads.

:evil:

---

### Post by gerowen on 2012-11-07
As promised, here's the video demonstrating my method of wiping a hard drive of any residual data when it refuses to co-operate with my computer.

Video:
[http://youtu.be/pPBiFaTuKVc](http://youtu.be/pPBiFaTuKVc)

---

