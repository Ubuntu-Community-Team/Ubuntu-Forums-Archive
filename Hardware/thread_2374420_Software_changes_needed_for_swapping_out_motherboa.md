---
title: "Software changes needed for swapping out motherboard?"
date: 2017-10-16
forum: Hardware
---

### Post by David4321 on 2017-10-16
Hi, I need to swap out my motherboard for an upgrade, I have the new one here on hand. I want the operation to be as quick, clean, and painless as possible. Are there any software changes I should be aware of before attempting swap?

My system: 
250gb SSD HD with OS and limited personal data.
2 large data drives
Ubuntu 16.04 LTS 64 bit

Will I have to reinstall OS, or will it still work after swap?
Any other cautions or tips?
I assume data drives will be unaffected, yes?

Thank you

---

### Post by Bucky Ball on 2017-10-16
I would take the data drives out or at least unplug them for this. Good idea to have reliable backups on hand anyway. Just leave your OS drive plugged in.

Swap out the motherboard; plug everything in that needs to be, including your OS drive; switch on and see what happens. Unlike Windows, the drivers for your motherboard are (should) be in the kernel already, you don't need to install them individually using 25 digit authentication codes(!), so it should 'just work' out of the box. Are you changing video card or wireless card? If not and they are currently working, should be all good.

(*Note: It may throw an error if you have lines for the partitions on the data drives in the /etc/fstab file and those drives/partitions are not present at boot. Ignore or switch off and plug in the data drives then try again. If you it boot to the desktop without throwing an error, switch off, plug in data drives and reboot. See what happens.) 

No need to reinstall OS. Swap MBs, plug in OS drive, boot up and it should work fine. Let us know what happens. If there's any issues, hopefully an easy fix. Good luck. ;)

(A caveat to this is if your motherboard is very very new and 16.04 doesn't have the drivers for it. If this is the case, 17.10 might. I would do a search for the motherboard and Ubuntu online before proceeding anyway and see what you find. Others will have had experiences no doubt.)

---

