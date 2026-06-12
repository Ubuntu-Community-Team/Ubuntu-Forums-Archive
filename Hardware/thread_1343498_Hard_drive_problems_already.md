---
title: "Hard drive problems already?"
date: 2009-12-01
forum: Hardware
---

### Post by QuintusFabius on 2009-12-01
I just recently purchased this HDD for my new i5 XP/Karmic build.

WD6400AACS: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136298](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136298)

and while most everything has been fine and dandy for just under a week, today I started seeing some problems and am looking for advice.

When I logged into XP just now, it began popping up many alert bubbles saying that various files were corrupted and that I needed to run chkdsk.exe - so I did. It seemed to do quite a lot of work when it got to phase 2 (indexes) and then closed. A computer game of mine had it's latest few saved games mysteriously gone or corrupted, and when I tried to load a different game through steam, it wouldn't open. I followed steps on their website to recover this but it involved deleting files in the /steam/ folder... one of which windows can't delete because it's "corrupt". I then booted into karmic and mounted my windows partition - karmic couldn't delete the file either!

So far I haven't seen any problems in Ubuntu though. What should I do? Is this a clear indication that the drive is bad? Any way to be sure?

Thanks in advance!

---

### Post by PRC09 on 2009-12-01
Could you have picked up a virus or some sort of malware on the XP install?

---

### Post by QuintusFabius on 2009-12-01
Perhaps. I've only had the computer a few days, and either the windows firewall or zone-alarm has been running the whole time. I haven't installed much, and downloaded less. All from trusted sources (just steam, 7zip, firefox, flash, zonealarm, and a few drivers from nvidia and asus).

When i tried to delete the one file in /steam/ that wouldn't delete, in ubuntu, it seemed to think it was a folder. When i tried to delete it, it thought the file didn't exist, when i double-clicked it, it opened into a folder of my music! That doesn't sound like a virus does it?...

Also, I ran a short self-test with the ubuntu disk utility (running extended now) and it claims there are 0 bad sectors on my disk.

---

### Post by ramjet_1953 on 2009-12-02
Go to the Western Digital site and download the diagnostics software.

Run a check on the drive with it.

There are people who are having problems with ext4, which is used by default in Karmic.

I over-rode this and used ext3.

Regards,
Roger :D

---

### Post by QuintusFabius on 2009-12-02
> **ramjet_1953 said:**
> Go to the Western Digital site and download the diagnostics software.

Run a check on the drive with it.

There are people who are having problems with ext4, which is used by default in Karmic.

I over-rode this and used ext3.

Regards,
Roger :D

Good idea. I haven't had any problems with ext4, sofar linux has been running perfectly - the only problems i'm having in this area are on the ntfs partition it seems. I ran palimpsest and it doesn't seem to be showing any bad sectors, so a friend suggested running ntfsresize -fi /dev/sda1. He said that if there truly were no bad sectors then maybe it was a bad ntfs filesystem? Does that sound likely?

What could cause filesystem corruption that isn't because of bad hardware? I'd be worried it would happen again!

---

### Post by PRC09 on 2009-12-02
I really dont understand how your music files would end up in your game folders unless you have been moving files in XP around with your Ubuntu install.A quick search on the steam site for corrupted and missing game files seems to indicate you are not alone with that problem.Just curious as to which anti-virus software do you use?

---

### Post by QuintusFabius on 2009-12-02
> **PRC09 said:**
> I really dont understand how your music files would end up in your game folders unless you have been moving files in XP around with your Ubuntu install.A quick search on the steam site for corrupted and missing game files seems to indicate you are not alone with that problem.Just curious as to which anti-virus software do you use?

Well, I have been moving files around on both partitions in ubuntu, but I don't think that caused my problem - I do think I have it figured out now.

I don't know which virus software I use - I just installed XP a few days ago. A problem I was having with an old version of java letting in a vundo virus was one factor that made me switch full-time to ubuntu around a year ago. Since then I haven't used XP enough to need a virus program. Any you recommend?

As I said, I think I have this problem figured out. Somehow my NTFS filesystem got seriously corrupted (probably a hard shutdown I had to do early on... maybe) and it just needed to be fixed. My HDD had 0 bad sectors, so that wasn't the problem. ntfsresize -fi was showing 2000ish problems with my XP partition, so I ran "chkdsk.exe /f" in windows and all those problems went away. I was then able to delete all extra files in my /steam/ folder and it rebuilt itself quite nicely. Everything works now.

If anyone else finds this thread and has similar problems: try running palimpsest. If it shows no bad sectors, run ntfsresize. If that shows problems, you probably just corrupted your filesystem in a fluke accident - run chkdsk.exe /f to repair these errors!

Thanks for the help everyone.

---

