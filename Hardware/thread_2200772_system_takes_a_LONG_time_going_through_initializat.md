---
title: "system takes a LONG time going through initialization"
date: 2014-01-21
forum: Hardware
---

### Post by squakie on 2014-01-21
I honestly didn't know how to word a title for this.  On one of my ubuntu boxes (older core2-duo) I have a 750gb SATA drive, a SATA DVD-RW, and 2 old 160gb IDE drives.  I have a AMD hd6450 as the video card.  After installing ubuntu to the 750gb drive I checked the old IDE drives and they were not formatted or partitioned. So after loading the appropriate video driver for ubuntu, I then went on to install Windows XP on one of the IDE drives so I could use my family history software (wireless connection will be shut down in XP as soon as I am finished).  As soon as XP installed, and never before hand, the POST process now takes over 2 minutes with no messages, no response to keystrokes, nothing.  A USB ntfs drive that is connected also stops flashing and just stays on solid while all of this is going on.  After that over 2 minutes it moves on to showing the devices connected and continues on to normal boot.  I've run the memory check many many times and for long periods of time, and no errors are found.  I *think* it is somehow taking a long time for the now-XP drive to respond on POST - just a guess.  It does seem as if it is stuck at trying to identifying the drives before it finally moves on.  I've checked the BIOS for any stray settings but have found nothing that to me appears to be out of the normal.  Can anyone give me any pointers on how to try to troubleshoot this?  Should I start by disconnecting the IDE cable at the motherboard?

I know this isn't an ubuntu specific question, but is hardware, so I hope it was okay to post this here.  If not, I hope an admin will move it to the appropriate forum.

Thank you

---

### Post by carl4926 on 2014-01-21
Dunno
Legacy USB setting rings a bell

---

### Post by squakie on 2014-01-21
Hummmmm.... I don't remember even seeing that in the BIOS - and every system I've had for years has always had it - soooooo - I may have missed that!

I'll go checking - thanks for the input!

---

### Post by squakie on 2014-01-21
Well, I unplugged my external USB drive and indeed it booted fast again, so I went hunting for the option.  Only thing I could find was "USB 2 Controller".  I was set on "enabled", so I set it to "disabled" (the BIOS notes said when disabled, the BIOS will detect a high speed device and support it).  Plugged the external USB drive back and boom, it booted quickly again.  Only 1 "small" side effect I hadn't counted on - after disabling that option my wireless keyboard and mouse no longer work.  I don't have a wired keyboard or mouse anywhere ;)  - can't even enter the BIOS setup to try to fix it and live with a slow POST until I figure something else out ;)

Right now I can't get out to get a cheap keyboard/mouse to get me through - someone cut me off in traffic late this afternoon, right when the car in front of me decided to stop.  I had no choice - had to hit the center island instead of hitting a car.  So, I have a dented wheel (which I'm sure also means it's out of round), a busted up wheel cover, and a tire I fully expect to be flat by the morning.  And it decided to get cold again.......not changing a tire in the cold! ;)

At any rate - that appears to be the problem.  I just need to work out how to keep my wireless keyboard and mouse figured out with it.

Thanks!

---

