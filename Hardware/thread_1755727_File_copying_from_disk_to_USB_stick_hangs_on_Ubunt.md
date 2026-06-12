---
title: "File copying from disk to USB stick hangs on Ubuntu 10.10"
date: 2011-05-11
forum: Hardware
---

### Post by kasun04 on 2011-05-11
Hi all,

I'm having Ubuntu running on my dell XPS1330. When I try to copy a file (~1GB) from disk to USB (Kingston) stick, it always hangs during the file operation window (goes up to ~90% of the data transfered, but never get completed). Check with different USB sticks, but the problem persists with all of them. Any thoughts on resolving this annoying issue? 

Ubuntu 10.10 - the Maverick Meerkat

---

### Post by Paddy Landau on 2011-05-11
Hang in there. The copy goes off to the stick, and the stick does all kinds of things inside (I believe it's to do with wear levelling, but I could be wrong).

It will get to 90% or so, then appear to hang. But the USB disk is working like crazy to complete the copy. When I copy 100Mb, it takes a good couple of minutes, so you might need to wait 10 minutes or more for a 1Gb file.

Next time, get a USB stick with a light that flashes when it's working. Mine does that, so I know it's not hanging.

---

### Post by kasun04 on 2011-05-11
Thanks for your explanation.. Tried with a file around 100MB and it took 3-4 mins. Any idea on improving this?

---

### Post by Paddy Landau on 2011-05-11
> **kasun04 said:**
> Any idea on improving this?
Get an external hard drive instead, unless you need the small size.

USB sticks use a certain type of technology, and it's slow (well, compared to today's hard drives; they're lightning fast compared to the floppy disks of yesteryear).

Actually, I vaguely remember seeing a miniature hard drive in a USB-stick size, but at a high price.

---

### Post by BoomShaka on 2011-05-28
lol. win7 doesn't behave like this when I copy the same file across. Just sayin'

The least I would expect is an accurate progress bar.

---

### Post by Paddy Landau on 2011-05-29
> **BoomShaka said:**
> win7 doesn't behave like this when I copy the same file across.
Are you saying that Windows 7 copies the file across quickly, whereas Ubuntu does so slowly? If so, you may want to raise a bug report.

> **BoomShaka said:**
>  The least I would expect is an accurate progress bar.
I don't believe that's possible; as I understand it, the USB stick uses its own caching method and does not report the progress accurately to the operating system.

---

### Post by gotsanity on 2011-06-02
From the research I have been doing this seems to be a known bug that has been going on for around 5 years or so. Ive been hunting like mad to find an answer to the problem but cant seem to find one.

---

### Post by BoomShaka on 2011-06-02
> Are you saying that Windows 7 copies the file across quickly, whereas Ubuntu does so slowly? If so, you may want to raise a bug report.
No, that was more a comment in frustration. But I guess I meant Win7 copies the file, with a fairly accurate progress bar. Although it does seem to copy faster too.

> I don't believe that's possible; as I understand it, the USB stick uses its own caching method and does not report the progress accurately to the operating system.
Again, I hate to harp on about Win7, but the progress bar fills at a steady pace. In my ubuntu install it gets to 90/95% and then sits there for an undetermined amount of time.

> From the research I have been doing this seems to be a known bug that has been going on for around 5 years or so. Ive been hunting like mad to find an answer to the problem but cant seem to find one.
Yes, I moved back to Win7 in the past due to issues like this, but I guess it hasn't been resolved yet. I only recently returned to Ubuntu because I prefer it as a dev environment to Win7 (and wanted to try 11.04), but issues like this may just drive me back to Win7. :(

---

### Post by my2234 on 2011-08-06
I know what you mean about getting driven back to Windows.
 I am having similar problems with my USB Western Digital 1TB drives.  
 Sometimes file corruptions in addition to freezing, which is not surprising as UBUNTU at times hangs during file copies. Also if I try to safely remove the drive UBUNTU often hangs.
 I often have to resort to using Windows XP to fix my damaged file structures.
 There is a real need to get these types of problems fixed. Buggy file transfers are just not acceptable in an operating system, as often there is no error raised and you only find out there is a problem when you try to read the file.  
 USB file transfers seems to have been a problem area in UBUNTU for years now.
 The same devices work flawlessly on Windows XP. You have no idea how much I hate saying that.

---

### Post by Paddy Landau on 2011-08-06
> **my2234 said:**
> ... Sometimes file corruptions in addition to freezing ... I often have to resort to using Windows XP to fix my damaged file structures...
Please raise a bug report so that the developers know. Post the link here so that people can vote for the bug.

---

### Post by itismike on 2013-04-04
> **Paddy Landau said:**
> Please raise a bug report so that the developers know. Post the link here so that people can vote for the bug.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1131858](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1131858)

---

### Post by oldos2er on 2013-04-04
Old thread closed.

---

