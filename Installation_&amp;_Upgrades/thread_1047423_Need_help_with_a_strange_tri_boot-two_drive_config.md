---
title: "Need help with a strange tri boot-two drive configuration"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by Crashing on 2009-01-22
Right now, I am downloading Windows 7 beta. The computer that i want to install it on runs XP on the primary HD and Ibex on the slave HD. I would like to install 7 on the slave HD because it has 80GB of space and the master drive is a 40GB. I can partition the drives, but I would like to know if 7 will show up in the GRUB boot menu if I install it on the 80GB HD.

---

### Post by logos34 on 2009-01-22
If grub is on the master, I believe all you'll have to do is add win7 to menu.lst like [this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").  But if the boot drive is the slave, win7 will overwrite grub with it's own and you'll have to restore grub using the live cd (see link in my signature).  So, either way you'll have to add win7 to menu.lst and possibly restore grub to the mbr.

---

### Post by Crashing on 2009-01-22
Grub is on the slave hd. I don't mind having to restore grub, but will XP not work until I get grub up again, or will 7 revert to the mbr and just give me a choice between so and 7 at bootup?

---

### Post by caljohnsmith on 2009-01-22
In addition to what logos34 said, I just wanted to mention that in my experience, Windows typically won't install to a slave drive unless you have a primary NTFS/FAT partition available on the *master* drive where Windows can put its boot files. I don't know if that has changed with Windows 7, but I suspect it hasn't because of the limitations of Windows boot loader. So you might have to temporarily set your slave drive as master just to install Windows, and then afterwards add an entry to boot Windows in your Grub's menu.lst like logos34 all ready suggested. If you don't do that, Windows 7 will probably put its boot files in the XP partition on your master drive, and take over the booting process for both XP and Win7. Good luck and let us know how it goes.

---

### Post by Crashing on 2009-01-22
That is a very good idea! I will do it that way so I can keep the xp partition intact. I will definately let you guys know how it goes. Just in case there are more ppl out there with such a wacky os configuration.

---

