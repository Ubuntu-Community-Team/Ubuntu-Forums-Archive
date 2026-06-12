---
title: "Frequent drive errors leading to root partition being remounted read-only"
date: 2010-05-15
forum: Hardware
---

### Post by emilywind on 2010-05-15
My hard drive has been randomly remounted read-only about one to two times per day for the past few days. I am using Lucid Lynx with all the latest updates and a fairly vanilla installation, and it usually happens when watching a video. My instincts say it has something to do with using Transmission, but it also happened when I was working on writing my book in OpenOffice at one point and Transmission was not open at the time. I also encountered this issue in a previous installation of Ubuntu from a long time ago, although less frequently. With my recent previous installation of Lucid on a 20GB portion of the hard drive, this never happened.

What I am wondering is why it is happening so often and what would trigger it. According to SMART, there are no bad sectors on my drive and I always have fsck fix the drive after rebooting due to the issue. This never happened when I ran Arch Linux on here a bit over a year ago, nor did I have any such issues with Windows 7 or OS X on the same machine. This is getting rather bothersome, but I do prefer to use Ubuntu and do not want to switch to other stuff just to avoid it. Any thoughts?

---

### Post by emilywind on 2010-05-15
Well, this has been shoved several pages back and still no response. Any ideas on what's going on at all?

---

### Post by emilywind on 2010-05-17
I found more information on the issue, although it just seems like it is a bug from times past which has yet to be resolved. How fantastic.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438379](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438379)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438379/comments/15](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438379/comments/15)

I also found a similar issue reported by a user back in 2008. I like using Ubuntu, but I also like my system running without having to reboot due to random file system issues every day. It would be amazing to see some people respond to this issue, particularly developers, but if not and it persists then well... Fedora 13 is released in 8 days.

I would rather not hassle with installing a new OS, but stability is very important, especially when it comes to insuring the safety of my data. I am an author along with a student, and therefore I have books I am working on stored on my laptop. I already lost some content of one when this happened while saving the file in OpenOffice.org, and although I wrote it all back and keep backups elsewhere, it was not a happy moment for me and I should not have to worry about stuff like this happening on a daily basis at all.

---

### Post by emilywind on 2010-05-17
Help on this topic would be much appreciated. Still out in the cold here.

---

### Post by GUmeR on 2010-05-18
Welcome in the club.

This is kernel bug. Not sure if reported.

Here is more:
[http://ubuntuforums.org/showthread.php?t=1475124]("http://ubuntuforums.org/showthread.php?t=1475124")
This guy has exactly same issue, as I:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515937]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515937")

Could you provide more info? 
1. What pc is it? By any chance LENOVO laptop?
2. What file format? ext3? ext4?
3. 32/64bit, kernel version:
```
uname -a
```
4. Most important, Dmesg output, you have to do that after your system gets remounted read-only.
```
dmesg
```

You are not alone :)

EDIT:
About data security: My system partition is ext4, I have other one, for data/movies/etc which is ext3. Scenario: I watch movie from ext3 partition, I get HDD error, root partition gets re-mounted read-only. Funny thing is ext3 is still read-write, I can save whatever I want there, few times I did, and data was OK. I know it doesn't sound super-safe, but still better than loosing work.

---

### Post by emilywind on 2010-05-18
Yeah, next time this happens I plan on saving whatever I am working on to a flash drive or my external drive, but at the time it did not occur to me to do that. Regardless, I am not a fan of workarounds in place of the actual solving of an issue so hopefully this is fixed soon. :)

---

