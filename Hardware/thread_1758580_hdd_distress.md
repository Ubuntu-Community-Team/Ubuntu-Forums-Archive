---
title: "hdd distress"
date: 2011-05-14
forum: Hardware
---

### Post by Ormond on 2011-05-14
i have a dell inspiron 6000 laptop and the hdd is going bad.  i found out when my windows (previous operating system) would not load.  i switched to ubuntu and was informed right away that the hdd was failing.

i decided to try to partition my 1 T ext hdd and install an operating system on it so that i could use that with my laptop in place of its hdd. 

i did manage to partition it with the disk utilities here on ubuntu and thought that i had installed the operating system.  i set up the boot sequence to start with the usb but it does not boot up.  i tried hooking up the external to my desk top and all it sees is the partition i made for the os, full of files but does not see the other 750G partition.

is what im trying even possible?
should i be using the side usb port instead of the back one?
do i need a 3rd partition with some kind of boot commands or something?

i may be ignorant and asking a stupid question but i hope that is not the case and someone can help.

---

### Post by PhantmKllr on 2011-05-14
I remember that certain partition types (I think swap, but I'm not sure) can't be read over USB. This would prevent you from booting from the external drive.

---

### Post by BertN45 on 2011-05-14
You don not need the SWAP, I have installed Ubuntu without the SWAP more then once, but you need enough memory say 1GB or more.

Did you remove the failing disk from the laptop? Your boot loader is probably on your failing disk, does it show a grub menu when you boot? The second entry might boot from your usb drive.

If you install the OS you should choose the manual/advanced partitioning and select that the grub boot loader is put on the usb drive.

---

### Post by dandnsmith on 2011-05-15
Did you check that the laptop will boot from a USB device at all?

If it does, perhaps there is something with this external HDD which isn't acceptable for booting (I recently tried to run a Sony VAIO from a USB stick - only one of my collection would work, which happened to be a 1GB device, while others were treated with contempt - but work perfectly on some other PCs)

Last thought - is there a proper filesystem on that 750BG?

---

