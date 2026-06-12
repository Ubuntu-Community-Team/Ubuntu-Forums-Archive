---
title: "No keyboard/mouse after aborted upgrade attempt to 9.04"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by jbrosenberg on 2009-05-03
Hi,

I was in the middle of doing the upgrade from 8.10 to 9.04 over the network, when my system shutdown (it appears to have overheated due to a faulty cooling fan).  I've installed a new fan, and tried to bring my system back up, and it appears to bring me to the usual 8.10 login screen.  The only problem is that the keyboard/mouse no longer respond.

I am able to use the keyboard to enter the BIOS when initially powering up, so I know the keyboard is functional.   But once it boots up, I can no longer login to the main gnome prompt.

The upgrade had not gotten close to completing when it shutdown, it had about 50 minutes left according to the progress meter to complete the upgrade.

Is there any hope to recovering my system and getting the keyboard/mouse going again?

Do I need to intercept the starting of the gnone/X11 on boot, and login on the console?  How can I do that?

It doesn't appear to have started the network at the point where I lose the the keyboard/mouse, so I can't remote log into it or anything....

Assuming I can get back into the system, do I need to edit the Xorg.conf file, or some such?

It's an older system, and uses ps/2 mouse/keyboard jacks, etc....

I would have thought that until the upgrade completed, and the system rebooted, I should have been able to revert to the previous OS without issue, but apparently not?

Thanks for any insight....

Jason

---

### Post by jbrosenberg on 2009-05-03
I've been able to get into the Grub loader, and boot the latest kernel in recovery mode...

I've tried all the different options, including fsck, cleaning of packages (where I was able to discontinue the Upgrade in progress, etc.)....

I also tried booting with previous kernels listed there, I tried changing the xorg.conf to previous version, etc....

Any other ideas?

Jason

---

### Post by upchucky on 2009-05-03
back up your home files, and re-install due to power fail there could be problems later on that will give you much grief.

when the power failed everything sitting in ram was lost and never got written to the drive, errors will come up in future.

---

### Post by jbrosenberg on 2009-05-03
Yeah, 

I'm resigned that I'll need to just re-install....

I'm a bit unsure as to how back up my files, I have no network, and my current system and user space is all on the single main partition....

thoughts?

Jason

---

