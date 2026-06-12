---
title: "Grub does not boot after update"
date: 2009-12-26
forum: Hardware
---

### Post by Ouoertheo on 2009-12-26
Hi guys,
I need a little assist on getting my netbook to boot ubuntu netbook remix 9.10 after an update seems to have broken my grub bootloader.

I just ran some updates (there were around 100, apparently it had been a while) and after the updates finished, I can no longer boot into ubuntu. I get to the boot menu, and then when i hit enter on the netbook remix entry, it just dumps me into a grub cli.

dont really wanna mess with anything in there not knowing what i'm doing, so does anyone have any helpful advice they could throw my way?

Thank you

---

### Post by yelvington on 2009-12-26
[https://help.ubuntu.com/community/Grub2#Command](https://help.ubuntu.com/community/Grub2#Command) Line & Rescue Mode may be of some help.

I had a more severe problem: Windows 7 trashed my boot sector; had to boot from USB, mount my drive, and reinstall Grub. Instructions were not hard to find with Google.

---

### Post by Ouoertheo on 2009-12-26
Thanks yelvington, so i set this up using wubi (using windows xp), and im not sure which partition it would be (since technically it's not a partition, it's an image)

i type in ls and it identifies two different partitions
hd0 and hd0,1 - im guessing hd0,1 is the one i want to get it to boot up to when selecting ubuntu right? i actually tried a couple of the suggestions on that page, but didn't get very far.

i think that ubuntu added a new kernel when it auto-updated, and i'm not too sure where to find which kernel i need to be looking for to try some of the things on that page that was provided.

wish i could find a way to peek into the image thru windows so i could see which kernel.

---

