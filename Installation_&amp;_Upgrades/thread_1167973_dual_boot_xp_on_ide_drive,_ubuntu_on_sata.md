---
title: "dual boot xp on ide drive, ubuntu on sata"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by BartlebyScrivener on 2009-05-23
I have been reading dual boot with 2 hard drive threads. Confusing! I am posting this just in case someone has been here before. I have a fresh install of XP on an oldish IDE drive (which Windows sees as Drive D). I have a new SATA drive where I'd like to install Ubuntu (Windows sees it as C: but it's raw or unformatted). 

I am at the "Prepare Disk Space" screen of the Ubuntu installation. As long as I have "Install Them Side by Side selected" the Install program sees XP and the IDE drive and the SATA drive below it.

If I select the SATA drive and "Use entire disk" or "Use largest continuous free space" for where I want to put Ubuntu 9.04, it says at the top, "This computer has no operating systems on it." I'm guessing that if I install this way, when I reboot, I won't be able to select XP at a boot menu?

What to do?  Must I specify partitions manually or something?

Thanks for any help.

---

### Post by logos34 on 2009-05-23
I'm guessing it looks like this:

[IMG]http://www.psychocats.net/ubuntu/images/installingjaunty09.png[/IMG]

if so that's normal.  Just make sure in the dropdown box you select the sata disk/correct drive letter.

A few screens later you should come to this screen:

[IMG]http://www.psychocats.net/ubuntu/images/installingjaunty11.png[/IMG]

Press 'Advanced' lower right and change the Grub location from '(hd0)' to '/dev/sdb' or whatever the sata drive is.  This will write the bootloader to the MBR of the sata, and leave windows bootloader on the IDE intact.

When installation is complete, reboot, enter the Bios and change the hard disk boot priority so the sata is first device.  Boot into ubuntu and do:

gksudo gedit /boot/grub/menu.lst

Edit windows entry at the bottom [like this]("http://www.users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk"), so you can chainload windows on the other disk.

Doing it this way means you can still boot directly into windows by changing the bios boot order.

---

### Post by BartlebyScrivener on 2009-05-23
Wow, PERFECT instructions.

Thank you so much.

BS

---

### Post by BartlebyScrivener on 2009-05-23
Quick follow-up for those who come after.

The instructions above are perfect. The crucial bit is to have grub installed to the Ubuntu disk only and NOT to the drive containing Windows. Then switch the boot order so that the Ubuntu drive goes first.

The editing of menu.lst was unnecessary. The Ubuntu installer took care of this for me. 

If it matters, this was an older motherboard MSI K8N Neo4.

Thanks for the always excellent support.

BS

---

### Post by logos34 on 2009-05-23
> **BartlebyScrivener said:**
> 

The editing of menu.lst was unnecessary. The Ubuntu installer took care of this for me. 


great.  sometimes it adds the 'map' lines, sometimes not

enjoy

---

