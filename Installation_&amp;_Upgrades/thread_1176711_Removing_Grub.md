---
title: "Removing Grub"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by thismango on 2009-06-02
Right, I am pretty sure Ubuntu is not compatible with my laptop (ASUS A6000) as I've tried 8 and 9 with no success. So I decided to reinstall Windows but I can't get rid of Grub. My recovery CD is not a Windows one, it's an ASUS disk that came with the computer, it's almost completely automated and doesn't have the recovery console available. The only option is an MS-DOS prompt.

I now have no working OS. Please help!

---

### Post by quixote on 2009-06-03
The MS-DOS prompt is kind of the DOS version of recovery console, so there's things you can do.  When you say you can't get rid of grub, do you mean that it keeps showing up when you try to boot? 

When you're at the DOS prompt (C: let's say) what shows up when you type 
```
C: dir
```

What's the problem you're having with the Asus recovery disk?  It won't boot from it?  It boots, but then it complains about something?

---

### Post by thismango on 2009-06-08
Thanks for replying.

When I try to use the recovery disk, it gets through most of the installation process. After it has installed the drivers, it asks me to remove the disk, then reboots. That's when the machine tries to boot from Grub, which it can't do any more so it gets stuck there.

The directory at C: is

SYSPREP <DIR>
I386 <DIR>
$WIN_NT$ ~BT <DIR>
$WIN_NT$ ~LS <DIR>
TXTSETUP SIF
$LDR$
NTDETECT COM
NTLDR
A6NE_A6G 20

Thanks.

---

### Post by presence1960 on 2009-06-08
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by thismango on 2009-06-08
Unfortunately the above thread refers to restoring from a Windows XP CD. I only have the ASUS recovery CD, which does not include the recovery console. The recovery console commands in that thread don't work at the MS-DOS prompt, which is the only option I've got.

---

### Post by Anger 2 on 2009-06-08
See the various methods on this site.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by thismango on 2009-06-08
I don't think I have any of those options. I can get either an MS-DOS prompt from my restore CD or I can get Ubuntu Live CD which won't connect to the Internet.(I know Ubuntu should in theory install OK if the Live CD will run. But it doesn't).  So I think I need to do it from MS-DOS. Does anyone know how to do this?

---

### Post by torgrot on 2009-06-08
If you have Windows XP and an old copy of a Windows 98 diskette you could use the commands from there fdisk/mbr and that would restore the MBR enough to complete your recovery.  Another possiblitiy would be to find someone to download and burn a SUPERBRUB CD for you and boot from that.
 
torgrot

---

### Post by quixote on 2009-06-08
There are two possibilities here.  (I'm not an expert, so you may need to do a bit more studying :( !) The first problem (1) is that you probably need to fix your Windows Master Boot Record. The second (2), which would I think go away if the first one was fixed, is that grub files are still hanging around on the system.

1) In the high and far off times you fixed  a faulty MBR by booting Windows from a floppy that had "fixmbr" on it.  At the A: prompt you ran fixmbr and the kind of problem you're having would sometimes go away.  I'm not sure what you'd have to do on an Asus, since it'll probably be even harder to find and attach a floppy than to rebuild Windows!  Maybe you could run it off any bootable external medium?  Try searching for "fixmbr ASUS A6000" (no quotes) and see if anything useful comes up.

2) Grub uses plain old text files, so once you find them, you can get rid of them.  It's been forever since I used DOS and I don't remember the command to find files. (Search for "MS-DOS find" maybe?) However, even if you get rid of grub, it sounds to me like the problem is your Windows boot record, so you still wouldn't be able to boot windows.

The instructions I can find looking around the Ubuntu sites are all about how to fix grub after Windows destroys it, not the other way around.  (Eg: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows))

Just remember: your files and operating system are there.  All you need to fix is the boot record.  This is do-able!  We just have to figure out how...:)

---

### Post by quixote on 2009-06-08
Supergrub is also a good idea. [http://www.supergrubdisk.org/w/index.php5?title=Boot_Problems](http://www.supergrubdisk.org/w/index.php5?title=Boot_Problems)  and the download site: [http://forjamari.linex.org/projects/supergrub/](http://forjamari.linex.org/projects/supergrub/)  I haven't used it myself, but it sounds very good.

---

### Post by sendblink23 on 2009-06-08
hmm weird

---

### Post by kayvortex on 2009-06-08
My experience of Recovery CD's is that they are all pretty stupid. I'd check how the recovery disk has "restored" your disk, exactly, by checking what partitions remain. But, then, that can wait I suppose.

To boot Windows all you need to do is "fix" the MBR (Master Boot Record). Do you have ANY old Windows CD lying around? If not, you'll probably have to download TRK (Trinity Rescue Kit), burn it onto a disk, and restore the MBR with that. Check to see if you have ANY Windows CD you can even borrow from anybody, first (you wont be installing windows from it, so you don't worry about serial keys: there's nothing illicit in what you're going to do with it).

Edit: Also, where exactly is the DOS prompt showing up? Doesn't the system just show some grub error about a partition not being found or something when you try to boot?

---

### Post by user_not_expert on 2009-06-08
> **torgrot said:**
> If you have Windows XP and an old copy of a Windows 98 diskette you could use the commands from there fdisk/mbr and that would restore the MBR enough to complete your recovery.  Another possiblitiy would be to find someone to download and burn a SUPERBRUB CD for you and boot from that.
 
torgrot

A Windows installation normally overwrites the master boot record. If the Assus recovery install doesn't do this, then it might be necessary to get an XP master boot record written somehow. I think the last time I tried using:

[fdisk /mbr]

on a broken XP boot record, the 98 boot disk successfully corrected the problem but the XP installation saw it as an old version. I then had to re-install XP which was now possible, and which overwrote it's own master boot record. It seems that this is not happening in this instance. This command is always worth a try though.

---

### Post by thismango on 2009-06-08
Yes! That was it. I had an old Win98 disk, got to the recovery console from there and used fixmbr. Trying the reinstall from my ASUS disk again now. So let's see what the next obstacle is!

---

### Post by thismango on 2009-06-08
That did it. I now have a functioning operating system and all of my hard drive back again. Thanks for all the advice, everyone.
Now the next step is whether I can get Ubuntu to work!

---

### Post by torgrot on 2009-06-08
Why don't you back your working system up before you try again.
 
torgrot

---

### Post by quixote on 2009-06-08
sendblink23: I got a copy of your very useful-sounding message in my email, but it's not here on the site.  Was there a problem with the command?  It sounds like a useful one to know.  Anyone know why it's gone?

---

