---
title: "my system boots through stage2 ?"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by 10ghost on 2009-09-06
hi readers and solvers,

I just installed on a partition of my computer opensolaris but before i in stalled i ran open solaris using its live cd. After booting i then installed it but i notice that during booting using the live cd it passed through the stage2 and this is not the normal root based on my experience so far.
I shutdown my computer normally and started it upo again expecting 2 see a list option of the operating system i wld like to boot into but to my surprise i realised that it did not but bypassed disapying on the black scrren stage2.I decided to continue and see what would happen it showed me a list of only one option showing just open solaris.
What could be the problem ? When it boots through stage 1 before installation of solaris it goes straight to my ubuntu o/s.
How can this be  resolved?
pls help me?

this might be a wrong question here but let me ask any way.
Why is it that i cant mount the ubuntu partition on solaris o/s.
This is also the same when i boot using a ubuntu live cd i am able to mount the ubuntu partition but not able for the solaris?
Is it because of the filesystem being used by both or what?

---

### Post by 10ghost on 2009-09-06
dont get my problem wrongly. I am an ubuntu user that installed open solaris to see how it feels and how both can work on the same system and what issues woulod one face doing this?

---

### Post by presence1960 on 2009-09-06
Do you mean you want Ubuntu's GRUB to load when you boot? if so when you installed Open Solaris you should have installed it's GRUB to Open Solaris's / partition not MBR. This is an easy fix but I need to see your exact set up. Do this please:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

I will then give you a precise set of instructions to get Ubuntu's GRUB when you boot and give you the entry to chainload Open Solaris from Ubuntu's GRUB

---

