---
title: "[SOLVED] Can play but not copy dvds"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by MeanderingCode on 2007-11-08
Hello, all.

Very odd behaviour, here.

I can play commercial DVDs just fine with vlc.  I can browse the files with thunar.

When i use k9copy or even dd (with /dev/scd0 or /dev/sr0 as input file), the proccess errors out.

/dev/sr0 is a link to /dev/scd0.

When i insert a dvd, here's the dmesg output:
```
[ 1142.044000] end_request: I/O error, dev sr0, sector 1248
[ 1142.048000] UDF-fs: Partition marked readonly; forcing readonly mount
[ 1142.048000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'E2938', timestamp 2007/01/23 09:48 (1e20)

```

when i try dd, here's the output:
```
myself@host:~$ dd if=/dev/sr0 of=./test
dd: reading `/dev/sr0': Input/output error
992+0 records in
992+0 records out
507904 bytes (508 kB) copied, 3.3104 seconds, 153 kB/s
myself@host:~$ dmesg
[ 1735.252000] end_request: I/O error, dev sr0, sector 996
[ 1735.252000] printk: 94 messages suppressed.
[ 1735.252000] Buffer I/O error on device sr0, logical block 249
[ 1735.252000] Buffer I/O error on device sr0, logical block 250
[ 1735.252000] Buffer I/O error on device sr0, logical block 251
[ 1735.252000] Buffer I/O error on device sr0, logical block 252
[ 1735.252000] Buffer I/O error on device sr0, logical block 253
[ 1735.252000] Buffer I/O error on device sr0, logical block 254
[ 1735.252000] Buffer I/O error on device sr0, logical block 255
[ 1735.252000] Buffer I/O error on device sr0, logical block 256
[ 1735.252000] Buffer I/O error on device sr0, logical block 257
[ 1735.252000] Buffer I/O error on device sr0, logical block 258
[ 1735.280000] end_request: I/O error, dev sr0, sector 1248
```

Clear dmesg, try w/ other device, still says device sr0 in dmesg

```
myself@host:~$ dd if=/dev/scd0 of=./test
dd: reading `/dev/scd0': Input/output error
992+0 records in
992+0 records out
507904 bytes (508 kB) copied, 3.15082 seconds, 161 kB/s
myself@host:~$ dmesg
[ 1947.728000] end_request: I/O error, dev sr0, sector 996
[ 1947.728000] printk: 62 messages suppressed.
[ 1947.728000] Buffer I/O error on device sr0, logical block 249
[ 1947.728000] Buffer I/O error on device sr0, logical block 250
[ 1947.728000] Buffer I/O error on device sr0, logical block 251
[ 1947.728000] Buffer I/O error on device sr0, logical block 252
[ 1947.728000] Buffer I/O error on device sr0, logical block 253
[ 1947.728000] Buffer I/O error on device sr0, logical block 254
[ 1947.728000] Buffer I/O error on device sr0, logical block 255
[ 1947.728000] Buffer I/O error on device sr0, logical block 256
[ 1947.728000] Buffer I/O error on device sr0, logical block 257
[ 1947.748000] end_request: I/O error, dev sr0, sector 1248
[ 1947.768000] end_request: I/O error, dev sr0, sector 1252
```

same dmesg with k9copy.  But i can get all the way through any number of movies in vlc, menu navigation and all.

Any clues??

===============================================================================================
SOLVED:

see [http://ubuntuforums.org/showpost.php?p=3395414&postcount=25](http://ubuntuforums.org/showpost.php?p=3395414&postcount=25)

```
vobcopy -v -m -o /path/to/output/dir
cd /path/to/output/dir
genisofs -v -dvd-video -o /path/to/put/filename.iso .
```
I used genisofs because the package details of mkisofs (suggested in thread linked above) say it's just a dummy transitional package for genisofs.
The dot at the end of the genisofs command is the path to the directory in which resides the VIDEO_TS folder.

The funny part of my vobcopy experience is that the program names files *.partial until it's done and then removes the .partial once it's done, but mine retained the extention.  I manually renamed them because genisofs (when using -dvd-video option for a udf filesystem) was looking for specifics it couldn't find, then created an iso which seems to be a full backup.  (I mentioned in post #7 that k9copy was backing up all menus and transition videos, but not the titles themeselves, for whatever reason).

Any insight on this .partial issue is welcome, as well as info on why dd doesn't work that way or why k9copy did what it did.
Thanks to [andrew.46]("http://ubuntuforums.org/member.php?u=208550") for his posts (one linked in thread above) and [MrFSL]("http://ubuntuforums.org/member.php?u=80341").

---

### Post by MrFSL on 2007-11-09
(Insert default warning about copying of DVD's being ILLEGAL in your country...)

I know I treading on shaky ground here in the forum, but I am pretty sure its not against the rules to say that you need to research the more recent DVD copy protections.

---

### Post by MeanderingCode on 2007-11-09
(Warning duly noted)

Copy protection aside, dd, when only passed input file and output file, simply reads bytes and writes what it sees, correct?

---

### Post by MrFSL on 2007-11-09
I am not inclined to help anyone break the laws of their own country - but information is and should be free. Plus you are asking now a question about dd and not about thieving DVDs

I will tell you that it is not that easy. It has to do with how disks are written and where on the disk information is written as well as other limitations. Copy protection is really genius when you think about it. Howdo we alter a disk so that it is still playable in DVD players, but not easily copyable by a computer. The answer is that these devices work differently. - Frankly (if I read the user agreement right) this is not the forum for discussing quasi-legal subjects.

The good news is that the information is out there. dd will NOT work for trying to backup most modern encrypted DVDs.

Try google.

---

### Post by MrFSL on 2007-11-09
I tell you what, here's a bone:
[http://en.wikipedia.org/wiki/ARccOS_Protection](http://en.wikipedia.org/wiki/ARccOS_Protection)

---

### Post by MeanderingCode on 2007-11-09
Thank you for your response about dd not working.  I don't know anything more about dd now, specifically whether or not i am right about the seemingly straightforward process of reading bits and writing them in identical order, though there is, i'm sure, plenty of documentation on dd out there that i can read.

> **MrFSL said:**
> I am not inclined to help anyone break the laws of their own country - but information is and should be free. Plus you are asking now a question about dd and not about thieving DVDs... Frankly (if I read the user agreement right) this is not the forum for discussing quasi-legal subjects.

While fair-use is still under much debate, pending years of court cases to set precedents on the matter, legality of certain actions is "quasi" clear.  Your assumption about theft is just that.  It may turn out illegal (if the MPAA, etc. get their way), but theft it is not to create a media computer that is connected to good speakers and display from which you play your owned music and movies from a library stored upon it.

> **MrFSL said:**
> I tell you what, here's a bone:
[http://en.wikipedia.org/wiki/ARccOS_Protection](http://en.wikipedia.org/wiki/ARccOS_Protection)

I don't know if this was intended to be rude, but "throwing a bone" is generally a derogatory phrase.  You don't need to be curt, sideways, or judgemental to keep yourself "safe" or in the clear.  You also don't have to post if you feel like the content is distasteful or of questionable merit or legality.

I'm sorry if i am misinterpreting your responses.

---

### Post by MeanderingCode on 2007-11-09
Just like to say for anyone reading this thread that i'm still stumped as to why this is happening.

For clarification and heading of some possible questions, it's a (non-Sony) multi-disc set that one disc worked, subsequent discs failed, now the one that worked won't, either.

I've been struggling with usb storage, too (running repository 2.6.22 kernel) with module ehci_hcd (works fine, but slow, once that's unloaded) and i'm beginning to wonder if this is a kernel problem.

Anyway, anyone with any idea why this might happen?

EDIT: Actually, that one that worked (k9copy) didn't actually work...i can get it to do what it did before, now:  make a small iso containing all the menus and transition videos, but none of the actual titles.  I was using the "backup" or "copy" function of the program, the size in the config was set larger than the disc was.

---

### Post by MrFSL on 2007-11-09
> I don't know if this was intended to be rude, but "throwing a bone" is generally a derogatory phrase. You don't need to be curt, sideways, or judgemental to keep yourself "safe" or in the clear. You also don't have to post if you feel like the content is distasteful or of questionable merit or legality.


Nope and I apologize if that is the usual meaning in your area. "Throwing a bone" is used differently I think - often used between friends and co-workers - Likened to "Lend a hand," or "Give me a hint."

---

### Post by MeanderingCode on 2007-11-10
> **MrFSL said:**
> Nope and I apologize if that is the usual meaning in your area. "Throwing a bone" is used differently I think - often used between friends and co-workers - Likened to "Lend a hand," or "Give me a hint."

Thank you.  Colloquialisms are odd, aren't they?  Most especially odd not being the formation of them, but the different meanings and forms the same phrases can take in different areas (i grew up in the midwest of the states).  The meaning i've known growing up has more to do with tossing a scrap useless to you to someone lesser as in tossing the leftover bone from the turkey leg to the dog on the floor in the corner, usually to satisfy them to get them off your back.

Anyway, I appreciate your clarification.

---

### Post by MrFSL on 2007-11-10
> Colloquialisms are odd, aren't they? They sure are! Furthermore it is hard to show expression when typing. Take it for granted that most people on this forum are trying to help you and are friendly though and you might find yourself not getting offended from comments like mine.

Honestly, I often ask co-workers to "through me a bone" meaning giving me just a small segment of what I need. Not the "meat" of it, but rather the "skeleton" to build upon. 

I tried to find the exact specs of DVD media so as to write or point to a simple explanation or proof-of-concept to no avail. I did run across this thread:
[http://ubuntuforums.org/showthread.php?t=387009](http://ubuntuforums.org/showthread.php?t=387009)

Also:
[http://www.discread.com/dvd-duplication/dvd-copy-protection-explained/](http://www.discread.com/dvd-duplication/dvd-copy-protection-explained/)
[http://www.dvddemystified.com/dvdfaq.html](http://www.dvddemystified.com/dvdfaq.html)

EDIT: It seems that the DVD FAQ (Link above) lists all the problems you can imagine concerning DVD. For instance:
> Serious DVD pirates can**_* copy the disc bit for bit, including the normally unreadable lead in *_**(this can be done with a specially modified drive), or copy the video output from a standard DVD player, or get a copy of the video from another source such as laserdisc, VHS, or a camcorder smuggled into a theater. It's certainly true that DVD piracy is a problem, but DeCSS has little to do with it.

It doesn't list information about some of the newer copy protections,  but it is still very good.

---

