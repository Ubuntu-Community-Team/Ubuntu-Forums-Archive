---
title: "Problem installing 8.10 and 9.04 (stuck at Configuring system locales)"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by unlimitedz on 2009-07-08
Hello everyone,

Ok so I wanted to install Ubuntu 9.04 yesterday on my PC.  I want to install it on a separate HD that I have, and leave my Windows XP partition alone.  Here is my current setup:

I have 3 internal IDE HDD's and 1 External USB HDD.

3 IDE:

Primary Master (200GB Windows XP)
Primary Slave (160GB Extra NTFS partition) - extra storage

Secondary Master (CD/DVD Rom drive)
Secondary Slave (20GB HDD) - This is what I want to install ubuntu on.

External HDD is a 500GB USB.

I also have a CD/DVD Burner connected via SATA (which is what i'm booting the Ubuntu CD from)

So I download the 9.04 x86 Desktop iso, burn it. then boot to it.  I do the integrity check and it passes no problems.  So i try and do an install, and everything seems to work fine.  I select the "Entire Disk" install, and choose the 20GB HDD, and away it goes.  It partition's fine, and copies the files fine.  Then when it gets to 78% and says "Configuring System Locales" it gets stuck.  First 2 times this happened I decided to leave it for awhile, came back about 45 minutes later and it was still stuck there.  Also the mouse is frozen and the keyboard seems to be as well.   I end up having to do a hard shutdown.

I figured it might be the iso i got, so I tried downloading the older Ubuntu 8.10, same exact thing happened (still passed the integrity check).

Not sure what the issue here is, And I don't know of any way to turn on a more verbose mode to see what's going on.  Anyone know what might cause this?

Thanks in advance!

---

### Post by unlimitedz on 2009-07-08
After reading around on the forums, I think that my next step should be to try the Alternate install CD.  I haven't tried this yet, but will when I get home today.

---

### Post by unlimitedz on 2009-07-08
Alternate CD did not work.  Now i can't even get to the install process, it just hangs after I select "Install" or even "Try ubuntu".

Any way to drop to a root shell and see what's going on?

---

### Post by unlimitedz on 2009-07-09
Ok after re-burning at slowest speed I was able to boot into the Live CD for 8.10.  Still when i try to install it hangs at 76%, but now the message is saying "Copying Files (less than a minute remaining)".

On the plus side, I re-burned 9.04 at the slowest setting.  When i go to install, it gets to 98% and freezes,  status message says "Configuring Hardware".

I've also tried both CD's with the noapic and acpi=off, one off and not the other, and vice versa.  Nothing seems to help.

---

### Post by unlimitedz on 2009-07-09
I was just successful installing 8.04 on the 20GB drive no problem.  I'm still confused as to why 8.10 and 9.04 don't work.

---

