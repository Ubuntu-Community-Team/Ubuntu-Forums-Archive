---
title: "A few problems with my 700m"
date: 2008-04-15
forum: Hardware &amp; Laptops
---

### Post by fndngemo on 2008-04-15
First of all I'd like to apologize for my complete ignorance when it comes to Ubuntu and Linux in general.  I installed it (8.04 beta) for the first time on my Dell 700m last night, and am still trying to learn my way around everything.  I have run into a few problems though that I'm hoping somebody may be able to help me with.  I tried searching for info but anything I found I couldn't really understand.  I'm hoping someone can explain to me in simple terms what I might be able to do to fix my problems.

First off, I'd say about 50-60% of the time when I shutdown my computer it doesn't actually shut down.  The screen goes blank and the system doesn't respond anymore, but the power LED is still lit.  The only way to shut down the system is to hold the power button for a few seconds until it turns off.

The second problem is that when I insert an SD card into my laptop the system appears to immediately freeze.  The mouse freezes and system becomes unresponsive.  The only thing to do is to hard restart by holding down the power button.  I've searched around and it seems like there are issues with the sd card reader working, but I couldn't find anything about it actually causing the system to freeze.

And finally, I'm having trouble with getting the laptop to suspend when I close the lid.  I adjusted the power management settings to have it go into suspend mode when on battery and simply blank the screen when plugged in.  Even when on battery though it seemed to just blank the screen when I closed the lid.  Out of curiosity I changed the settings for plugged in to go into suspend when the lid closes and the first few times it seemed to have worked.  Not how it should have, but at least it went into suspend when I closed the lid.  Now however it doesn't seem to suspend at all when I close the lid, regardless of the settings.  If I choose suspend from the shutdown screen it seems to work ok, just not when I close the lid.

Hopefully these problems are easy enough to fix for someone with knowledge, and any advice would be greatly appreciated.

---

### Post by fndngemo on 2008-04-15
bump, could really use some insight.

Thanks

---

### Post by aysiu on 2008-04-15
Ubuntu 8.04 hasn't been released yet, so if you find a bug, you should report it:
[https://bugs.launchpad.net/ubuntu/hardy](https://bugs.launchpad.net/ubuntu/hardy)

In the meantime, you might want to use an earlier version of Ubuntu (one that's been officially released), because apparently most things should work on the Inspiron 700m without much additional tweaking:
[https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron700m](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron700m)

---

### Post by jdkchem on 2008-06-03
The shutdown problem is not a "beta" issue.  From what I have been able to figure out the shutdown issue is related to acpi.  IIRC the solution is to put acpi=force in grub.  This may also fix your suspend/hibernation problem when you close the lid.

The shutdown issue is also a problem in Fedora 8 - 9 and with gutsy.

As for the card reader, it will probably never work.  Thanks TI:(

You might try going to [http://linux.dell.com](http://linux.dell.com) and check their repositories.  It may be that all you need to do is install one of the packages.  I don't know which one as I have not tried any of them yet.

---

### Post by Moistdef on 2008-06-22
Check out this thread in regards to the SD card reader: 

[http://ubuntuforums.org/showthread.php?t=165336&highlight=dell+700m+SD+card+reader](http://ubuntuforums.org/showthread.php?t=165336&highlight=dell+700m+SD+card+reader)

I too am having the same problems.

---

