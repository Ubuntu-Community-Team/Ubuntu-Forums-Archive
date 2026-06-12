---
title: "can't mount external hard drive"
date: 2010-10-21
forum: Hardware
---

### Post by mystmaiden on 2010-10-21
I lost my mind awhile ago and forgot to unmount my external hard drive before turning it off and now I can not mount it.

I'm running Karmic and the hard drive is NTFS.

This is the error message I get - 

```
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details
```I checked the disk with disk utility and it reports it as healthy. Is there a terminal command or some other work around to fix this? 

I tried running 

```
sudo mount -t ntfs-3g /dev/sdb1 /media/external
```it returns the same error.

thanks
mystmaiden

---

### Post by coffeecat on 2010-10-21
You cannot repair this in Linux. You have to use chkdsk in Windows. The comment about rebooting twice in the error message is assuming this drive is a Windows C: drive which, of course, it isn't. But you may need to run chkdsk more than once on it to repair it.

Do you have access to Windows?

**Edit:** sorry. Meant to add:

> **mystmaiden said:**
> I checked the disk with disk utility and it  reports it as healthy.

The disk is healthy but the NTFS filesystem in the partition is not. Hence the need to run chkdsk.

---

### Post by mystmaiden on 2010-10-21
Thanks for the reply, coffeecat. I don't have any windows access but a few more searches led me here:

[http://ubuntuforums.org/showthread.php?t=1333205&highlight=can%27t+mount+external+hard+drive]("http://ubuntuforums.org/showthread.php?t=1333205&highlight=can%27t+mount+external+hard+drive")

I ran ntfsfix and its good to go now!

edited to add:

Bah, I spoke too soon. It worked fine, I unmounted and remounted a couple of times to make sure but now, its Not working again...

---

### Post by coffeecat on 2010-10-22
> **mystmaiden said:**
> Thanks for the reply, coffeecat. I don't have any windows access but a few more searches led me here:

[http://ubuntuforums.org/showthread.php?t=1333205&highlight=can%27t+mount+external+hard+drive](http://ubuntuforums.org/showthread.php?t=1333205&highlight=can%27t+mount+external+hard+drive)

I ran ntfsfix and its good to go now!

edited to add:

Bah, I spoke too soon. It worked fine, I unmounted and remounted a couple of times to make sure but now, its Not working again...

Hmm. I was concerned that someone would suggest ntfsfix, and your forum search did indeed lead you to such a post. I'm sorry that there are people who are all too willing to recommend a utility who clearly haven't read  the man page for it. The man page for ntfsfix says:

> ntfsfix is a utility that fixes some common NTFS problems. [COLOR=red] ntfsfix is NOT a Linux version of chkdsk. It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows.[/COLOR] You may run ntfsfix on an NTFS volume if you think it was damaged by Windows or some other way  and it cannot be mounted.I've reddened the important bit. I'm sorry, but there's no way round this. NTFS is a Microsoft filesystem. Linux tools and drivers for it have of necessity been reverse engineered, and are in consequence incomplete, so there is no substitute for chkdsk for repairing NTFS. Do you have a friend or relative with a Windows system that you can use/borrow?

When and if you manage to get the filesystem repaired and your data recovered, I suggest you think of using another filesystem on the external drive if you do not have Windows easily available. If you need any help with this, do post back.

Good luck!

---

### Post by mastablasta on 2010-10-22
to run chkdsk you don't actually need the whole windows. if you maybe have a floppy drive you could make a windows floppy repair/recovery disk (or maybe you could try to make a repair CD?!).  Point is you will need something that will boot windows/dos and that you can put chkdsk on it in order to run it. maybe freedos can also be used. though i am not sure.
 
maybe you could have a look at this: [http://www.bootdisk.com/ntfs.htm](http://www.bootdisk.com/ntfs.htm)
 
here is a link for recovery CDs for WinXP: [http://www.ehow.com/how_4910631_download-windows-xp-recovery-disk.html](http://www.ehow.com/how_4910631_download-windows-xp-recovery-disk.html)
 
Either way you will have to get "down and dirty" with some MS programmes :-)
 
easiest option was already sugested - take the disk to somoene wiht windows on and let them do a chkdsk on the disk.

---

### Post by IcarusR on 2010-10-22
Hirens boot cd has 'mini XP' on it which has chkdsk.

Google 'hirens boot cd download'

---

### Post by mystmaiden on 2010-10-22
Thank you, coffeecat, Mastablasta and Icarus for the replies and suggestions. 

coffeecat wrote:

> When and if you manage to get the filesystem repaired and your data recovered, I suggest you think of using another filesystem on the external drive if you do not have Windows easily available. If you need any help with this, do post back.
I wondered about that when I purchased it, but the consensus seemed to be that it would work with linux, which it does - as long as you don't run into difficulties. If this is reparable, I'm not sure if the file system can be changed? Beyond that, is there an external out there somewhere that is made to work with linux? The chances of me ever going back to windows are slim to absolutely none.


I did finally get to access the files again, this by plugging it into my puppy linux machine and opening the files as read-only. Then back to the Karmic machine where I ran ntfsfix again and bingo it opened but when I tried to add a file,  6 movie vobs that I had so carefully copied from my dvds this week disappeared. I'm pretty sure they are still there somewhere but accessing them may never happen again.


Mastablasta wrote:

> to run chkdsk you don't actually need the whole windows. if you maybe have a floppy drive you could make a windows floppy repair/recovery disk (or maybe you could try to make a repair CD?!). Point is you will need something that will boot windows/dos and that you can put chkdsk on it in order to run it. maybe freedos can also be used. though i am not sure.I don't know anyone who would let me use their computer to fix this but I do have an ancient windows 98 box I dug out of the bottom of the closet, I can plug the external in, but windows 98 doesn't seem to 'see' it. I tried running chkdsk /f by entering  - 

```
chkdsk /sdb1 /f
```I may not have gotten the command exactly right. It said to use scandisk but scandisk didn't give the option of running it on the external.  I'm wondering if the 1tb hard drive is just too much for it. I did not try it in dos mode though. Unfortunately, everything I know about dos would fit in the back end of an ant. Is there a dos command I can use to have it look for the external?  I'm a bit nervous about trying to use any of the recovery programs on my karmic machine, I'd hate to accidentally wipe it out because the back ups are (you guessed it) on the external drive. Is there a way to (safely) go about it? 

thanks again,

mystmaiden

---

### Post by CharlesA on 2010-10-22
If it's a USB drive, a Windows 98 machine will probably not see it, since USB support back then was bad (not to mention that they didn't even have NTFS back then).

I know I've seen Windows recovery cds that you can boot off of to run chkdisk and whatnot, but I can't recall where I saw them.

EDIT: I guess I was thinking of this: [http://en.wikipedia.org/wiki/Windows_Recovery_Environment](http://en.wikipedia.org/wiki/Windows_Recovery_Environment)

---

### Post by mystmaiden on 2010-10-22
CharlesA-

 I hadn't thought of the fact they didn't have ntfs when the 98 was made, that does limit its usefulness - definitely! I'll look into the WRE

Icarus - 

The Hirens mini xp thing looks promising but the cd seems to have so much other stuff on it, its a bit mind boggling. So far I haven't found the link for the download, just kept going around in circles. Maybe it's on the torrents.

---

### Post by coffeecat on 2010-10-22
> **mystmaiden said:**
> I wondered about that when I purchased it, but the consensus seemed to be that it would work with linux, which it does - as long as you don't run into difficulties.

Yes it does work, but unfortunately you've run into difficulties.

> **mystmaiden said:**
>  If this is reparable, I'm not sure if the file system can be changed?

Easily done with either Disk Utility in the Administration menu or by installing Gparted. All you do is to reformat the partition, which changes the filesystem. But that has the effect of deleting everything, so you need to repair this filesystem first.

> **mystmaiden said:**
>  Beyond that, is there an external out there somewhere that is made to work with linux? The chances of me ever going back to windows are slim to absolutely none.

Not necessary. You simply reformat the one you have.

> **mystmaiden said:**
> I don't know anyone who would let me use their computer to fix this but I do have an ancient windows 98 box I dug out of the bottom of the closet, I can plug the external in, but windows 98 doesn't seem to 'see' it. I tried running chkdsk /f by entering  - 

```
chkdsk /sdb1 /f
```I may not have gotten the command exactly right.

As CharlesA said, USB support in Windows 98 was bad. And anyway, Windows 98 didn't support the NTFS filesystem (if I remember correctly) , which is why it didn't see it. Even had you been able to run the W98 version of chkdsk on it, you would likely have done more harm than good.

By the way, that code won't work even in XP. '/sdb1' in an incomplete Linux partition descriptor. You'd have to see what device letter Windows assigns it and then run 'chkdsk E: /f' or whatever.

> **mystmaiden said:**
>  It said to use scandisk but scandisk didn't give the option of running it on the external.

Forget scandisk. That was for detecting bad blocks before the days when hard drives could do this for themselves.

Long story short - you need Windows XP or later - or the Hiren CD if that's an option. Windows 2000 supported NTFS, but I would be happier with a later version of Windows to do this task.

There **must** be someone of your acquaintance who runs a recent version of Windows. If not, and if you live in a part of the world where Windows is rare or non-existent, I want to emigrate there. :p

---

### Post by mystmaiden on 2010-10-22
Thanks once again for the reply :)

coffeecat wrote:

> Long story short - you need Windows XP or later - or the Hiren CD if that's an option. Windows 2000 supported NTFS, but I would be happier with a later version of Windows to do this task.

The Hiren cd would be great if I could just find a place to get it, googling produces a link but there is no download on the page. They do not seem to sell it, either.  I'm at a loss.

> There must be someone of your acquaintance who runs a recent version of Windows. If not, and if you live in a part of the world where Windows is rare or non-existent, I want to emigrate there

Haha! Wouldn't a place like that be perfect! Truth is, I'm a bit of a recluse, I just don't know anyone. The times I venture past my front lawn are rare.

---

### Post by CharlesA on 2010-10-22
> **mystmaiden said:**
> 
The Hiren cd would be great if I could just find a place to get it, googling produces a link but there is no download on the page. They do not seem to sell it, either.  I'm at a loss.

I've always gotten them [here]("http://www.hirensbootcd.net/").

---

### Post by mystmaiden on 2010-10-22
Thank you, CharlesA. I was not looking in the right spot on the page, got it and burned it successfully.

I booted  the mini windows xp. It did not show the external under my computer, nor would it mount it when I clicked on the removable drive icon on the desktop, but when I left clicked the same icon it gave me a 'Reset NTFS Permissions CACLS' option. Clicking that netted - 

```
This will  REPLACE  all NTFS permissions to EVERYONE including all subfolders (or run the command manullally with E to edit ACL instead of replacing it. 

CACLS "x:\i386\System32\ShowDrive.exe" /T /C /G Everyone :F 
```That was followed by a Yes or No. I wasn't sure that was the right thing so I hit no, and shut down. Now here is the strange part. My external is working thus far since I rebooted in Ubuntu, with no error messages. It fooled me like that yesterday though so I'm wondering, do I need to go ahead and run the above command?

---

### Post by CharlesA on 2010-10-22
Sometimes it does that. I don't know how or why.

If it's working now, I'd leave it alone. The command in yer post will reset all NTFS permissions to "Everyone" which would negate any permissions on that drive (if you were to use it on a Windows machine at least).

---

### Post by WinRiddance on 2010-11-15
Well, I tried what mystmaiden suggested but it didn't work for me.
My initial error code has changed though, now I get this instead:

> Error mounting: mount exited with exit code 18: Failed to open ntfs attribute: No such file or directory
Failed to mount '/dev/sdb1': No such file or directory

Ah well ... :(
If anyone else is still experiencing the same issue after reading through this thread, then you might want to try this other thread that I opened up which also includes several options and hopefully a fix anytime soon now.
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10119258#post10119258](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10119258#post10119258)

Good luck.

---

### Post by CharlesA on 2010-11-15
What were you trying to do?

---

### Post by WinRiddance on 2010-11-15
> **CharlesA said:**
> What were you trying to do?

Hi there. If you're talking to me ... I'm trying to gain access to my external USB backup drive which I can't mount anymore, ever since I upgraded to Ubuntu 10.10 a few days ago. The initial error message was identical to the beginning of this thread, but then several things have been tried ... other than what's been mentioned here ... and so I figured I'd point people in that direction as well, just in case someone has the same issues that I'm still experiencing.

---

### Post by CharlesA on 2010-11-15
Ah. Didn't see the edit. I'll take a look at the other thread. :)

---

