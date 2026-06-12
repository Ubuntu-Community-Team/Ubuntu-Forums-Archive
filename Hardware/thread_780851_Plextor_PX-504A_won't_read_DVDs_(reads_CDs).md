---
title: "Plextor PX-504A won't read DVDs (reads CDs)"
date: 2008-05-03
forum: Hardware
---

### Post by zeerover on 2008-05-03
Ubuntu 8.04 (installed today, no other OS on system)
Intel D865PERL
2.4 GHz Pentium 4
2 Gigs RAM
160 GB Seagate SATA HDD
PLEXTOR DVDR PX-504A

**My Plextor PX-504A CD/DVD R/W combo drive will not see the contents of data DVDs.**

I just installed Ubuntu 8.04 Hardy Heron after wiping out a Windows XP system in which the drive functioned without any problems. Everything else in Ubuntu seems to work fine. The drive will read CDs (Music or Data), and it identifies DVD video but after downloading the recommended GStreamer plugins the player (Totem Movie Player) just crashes with the following error:

Could not open location; you might not have permission to open the file.

Data DVDs are recognized (a cdrom0 file browser pops up) but appear empty (there are no contents). This was the case both before and after trying the DVD video. I posted the error from the DVD video because maybe it suggests there's some sort of permission problem that might be relevant. I really don't know what to do. I'm new again to Linux after having used Mandrake from 2000-2002. Any help is much appreciated. I have googled and searched the forums for "ubuntu dvd won't read", etc., with no luck. Please let me know if there is any additional information I can provide that might help you help me.

Thanks!

 - Isaac

Update 1: Okay, it now seems to clearly be a permissions issue. I can ls the /cdrom directory but any attempt to peek at files (all of which are visible) gets a permission denied.

Update 2: My situation seems to be almost identical to [this unresolved thread]("http://ubuntuforums.org/showthread.php?t=729529") from one week ago. In my case CDs (data/audio) work but DVDs (data/video) get permission errors.

Update 3: Note the higlighted feedback:

```
$ ls -l $ ls -l /media
total 36
lrwxrwxrwx  1 root       root           6 2008-05-03 14:31 cdrom -> cdrom0
dr--r--r-- 40 [COLOR="Red"]**4294967295 4294967295**[/COLOR] 32164 2008-05-03 01:43 cdrom0
lrwxrwxrwx  1 root       root           7 2008-05-03 14:31 floppy -> floppy0
drwxr-xr-x  2 root       root        4096 2008-05-03 14:31 floppy0
```

What does this mean? Attempts to chown cdrom0 back to root are fruitless so far:

```
$ sudo chown root /media/cdrom0
chown: changing ownership of `/media/cdrom0': Read-only file system
```

?

---

### Post by zeerover on 2008-05-03
[deleted and consolidated above]

---

### Post by zeerover on 2008-05-03
(Cross-posted to [**CDROM Permissions screwed up?**]("http://ubuntuforums.org/showthread.php?p=4875822"))

Okay I think I'm on my way to a solution. I won't have time to write up a thorough explanation, or to work through all the kinks, but I did find the source of the problem and a half-decent workaround. It turns out that [COLOR="Red"]this has been a known issue in Ubuntu for 3 1/2 years[/COLOR] (no comment) that has taken a few slightly different forms. It seems to be best documented as [**Bug #10550**]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550"). For now I'll post [**Ric Flomag's helpful reply**]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550/comments/33") to that thread:

[INDENT]"[COLOR="Blue"][B]Quick fix: i have put iso9660 before udf in fstab to always mount dvds as iso9660:
/dev/hdc /media/cdrom0 iso9660,udf user,noauto,utf8 0 0[/B][/COLOR]
(the "utf8" option is a workaround to another long standing and very annoying bug, [https://bugs.launchpad.net/ubuntu/+bug/22623](https://bugs.launchpad.net/ubuntu/+bug/22623), but does not have any effect here.)

Totem now plays my DVD just fine. Obviously, this is not a good solution for everyone, but as i don't mind mounting my udf data DVDs as iso9660, it does not matter to me.

This bug as been here for a long time now"[/INDENT]

So this can be worked around by editing your /etc/fstab file to change the order from udf,iso9660 to iso9660,udf (not auto as some posters here have suggested, though they were clearly on the right track; likewise, the suggestion to fiddle with the utf-8 option was a right-minded trick that worked on a related bug, [**#22623**]("https://bugs.launchpad.net/ubuntu/+bug/22623")). What this does do is gives you access to protected discs (another way would be to format the relevant partitions in pre-protected file formats like fat32. 

A downside, however, is that these methods render the filenames in pre-sulfnbk.exe format, where longfilename.xxx becomes longfi~1.xxx (by chance I happen to have written something about this once: [**Sulfnbk Syndrome, Media Consumption, and the Dry Run that Wasn't**]("http://www.kuro5hin.org/story/2004/7/22/185750/629")). I think I can figure out a fix to this, or find a fix someone else has already figured, but I can't do it for a few days. For now I'm posting this reply, and cross-posting it to the thread I started, so that others can take advantage of the hack and maybe figure it all out without me doing any work. In any event I will post a thorough writeup once I have time, probably Thursday.

 - Isaac

---

### Post by zeerover on 2008-07-15
Nevermind. Ubuntu seems to just turn these and many other drives into duds. Bump. Anyone?

---

