---
title: "SATA Issue"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by abbot on 2006-06-06
It took me a while to figure out why Dapper wouldn't install on the same machine Breezy was doing fine on.  In the end I narrowed it down to my 2nd HD connected via SATA.

So this is what it's doing.  If I take the SATA card out Dapper works fine.  If I plug in the SATA card with the HD connected, it hangs during boot at "Mounting Root File System".  If I only have the SATA card in but no HD attached, it doesn't even get to the boot screen but just has a blinking cursor for a couple minutes then says "Invalid Boot Diskette: Insert boot diskette into A:"

I'd really like to be able to get the stuff off this HD.  I put everything that I needed on this SATA drive before I upgraded from Breezy.

Thanks In Advance.

---

### Post by abbot on 2006-06-10
This is really getting on my nerves.  A friend suggested using a different PCI slot but that didn't work.  Whenever I plug in the SATA card with my hard drive attached it hangs at "Mounting Root File System" for like 5 minutes then says

ALERT! /dev/hda1 does not exist.  Dropping to shell!

.... (version of shell etc..)

/bin/sh: can't access tty; job control turned off
#

I really need to get this drive working.  Is there something set up wrong where its trying to detect the SATA drive only and substituting it for my hda1 drive which it isn't seeing which has my OS on it.  If that's the case then how it is loading the boot screen and stuff when it says "Mounting Root File System"?

---

### Post by erikwithak on 2006-06-11
I have the same exact problem.
I couldnt even install dapper on my Dell because it stalled at "mounting root files system" then i turned off my second hard drive (serial ATA) and now it works fine. Except now i cant get to my music/movies and other random stuff i have on it. I hope someone can help us out with this

---

### Post by Bionic_Beefpile on 2006-06-12
On my system, the 2.6.15 kernel that Dapper ships with has this issue.  To get around it, I compiled the 2.6.16 kernel from source ([http://www.ubuntuforums.org/showthread.php?t=157560&highlight=compile+kernel](http://www.ubuntuforums.org/showthread.php?t=157560&highlight=compile+kernel))

I now have other issues, but at least I can boot

---

### Post by abbot on 2006-06-12
What are your new issues?  I don't want to do that if its just gonna cause worse problems.

---

### Post by Bionic_Beefpile on 2006-06-13
[QUOTE=abbot]What are your new issues?  I don't want to do that if its just gonna cause worse problems.[/QUOTE]

Heh, well now my CD drive doesn't work, although I am sure that it is because it's a SCSI drive and there is a problem with the 2.6.16 kernel's handling of it.

Even if you have the same problem, you can drop back to an older kernel, so you don't lost anything (except a little time) by giving it a shot.

And like I said, at least the system boots up now!

::EDIT:: and now I've fixed the CD problem as well

---

