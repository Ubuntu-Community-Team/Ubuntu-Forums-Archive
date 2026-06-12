---
title: "Tried Suspend, didn't wake up properly, now can't boot from HDD"
date: 2008-07-13
forum: Hardware
---

### Post by gaz514 on 2008-07-13
Hey people,

Just gone back to Ubuntu on my desktop after running Gentoo for a couple of years. I decided to give the Suspend feature in Gnome a try.

The computer went to sleep fine, and the power light flashed as it should. So I tried to wake it up again by pushing the power button. It started to wake up, the fans and drives and so on went back on, then the hard drive light went on and stayed on. After a few minutes it became clear that nothing was happening, and I couldn't hear any hard disk noise. So, since the system was stuck somewhere between suspended and awake so couldn't do anything, I pressed the reset button.

Now when I try to boot the system, it gets stuck right at the point where it's supposed to load Grub, the part where it shows the information about disks and the PCI device listing and IRQ assignments. So I can't boot off the hard disk. Booting off a CD works fine.

I tried checking the boot order settings in BIOS, as well as the graphics device setting (this caused a similar error before when I installed a WinTV card; changing the setting from PCI to PCI-E fixed it). I also ran the Ubuntu LiveCD, ran FSCK on all my disk partitions (no errors), and tried reinstalling Grub to the MBR.

Any ideas? Obviously the sooner I can fix this the better as I have an unusable computer.

If you're wondering, hibernate almost works perfectly but not quite, but that's for another time :)

My system:

Ubuntu 8.04 (64 bit)
Asus A8N-E motherboard, AMD64 3000+ (Venice) processor
1 gig RAM
NVidia 6200 graphics card, using nvidia driver.

---

### Post by gaz514 on 2008-07-14
OK, never mind, I fixed it.

The hard disk boot order in my BIOS settings had somehow changed, and so the system was trying to boot from my second HDD, as opposed to the first one which GRUB is on. Not sure what suspend had to do with this, but it works now so who cares.

I had already checked the device boot priority (cd, hdd, removable, network, etc.) but checking the hard disk boot order (a separate setting) only crossed my mind now.

Enjoying Ubuntu again :)

---

