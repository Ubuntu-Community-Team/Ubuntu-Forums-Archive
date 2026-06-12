---
title: "setting up a partition"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by chen74 on 2009-08-12
Hi I'm wanting to set up partition to duel boot 9.04 with Crunch bang. 

I've got 9.04 already installed but cant figure out how to to set up a partition inside of Linux. Can any one help as I managed to do it no problem with my Ubuntu vista machine but don't know how to go about doing it with linux installed first. 

Many thanks.

Ps 

Ubuntu and #! rock :O)

---

### Post by RedSingularity on 2009-08-12
Did you try the Partition editor in ubuntu?

---

### Post by fela on 2009-08-12
If you didn't partition 9.04 as ext4, you can use partition editor (on the Ubuntu livecd: System > Administration > Parition editor) to resize the 9.04 partition and make space for Crunchbang. If crunchbang automatically recognizes 9.04, you should probably let Crunchbang reinstall the GRUB bootloader. If it doesn't, you can add something like this to your /boot/grub/menu.lst:

title Crunchbang Linux
root (hd0,1)
kernel /boot/vmlinuz
initrd /boot/initrd.gz

Remember these are only generic lines and subject to change alot. I suggest if you want to manually add a Crunchbang menu entry, you read up on syntax of the grub menu.lst file.

Crunchbang should automatically find Ubuntu though and add it to its own GRUB installation.

Hope all goes well for you.

---

