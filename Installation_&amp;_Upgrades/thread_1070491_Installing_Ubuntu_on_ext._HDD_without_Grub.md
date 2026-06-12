---
title: "Installing Ubuntu on ext. HDD without Grub"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by Rubruquis on 2009-02-15
Hello everyone,
I want to install Ubuntu on an external harddrive and install Windows on the main harddrive ( C: ). And I don't want GRUB to load each time I start the computer. 
What I wanna do is that, when I will need to use Ubuntu, I will just plug in my external HDD and Ubuntu will load automatically. And when I will need to use Windows, I will just unplug the external HDD and Windows will load automatically.

I have tried this (installed Ubuntu on my external HDD and Windows on the main) and deleted Grub with fixmbr command. And changed the boot sequence from BIOS so that external HDD boots first. But after these, even when I plug-in my external HDD, Windows still boots automatically.

How can I solve this problem?

---

### Post by x33a on 2009-02-15
you'll have to change the boot sequence of your computer.

when you start the computer, press f2 key continuously, till you get into your configuration screen. here, find the boot sequence settings, and make the bios read the usb ports first, then the cd drive or the hard-drive (according to your choice). 

this way when you start the pc, your usb ports will be searched for bootable device, which is your external hdd, and boot from that.

---

### Post by Rubruquis on 2009-02-15
I have tried that but it doesn't work. Even if I choose external HDD as the first boot device, it still doesnt boot from the external HDD, it boots Windows.

---

### Post by x33a on 2009-02-15
after reading a few similar posts, i think it's not possible to boot ubuntu without a bootloader. (correct me if i am mistaken).

i think you can install grub on the ext. drive, and not on the internal drive. that way it might work.

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

