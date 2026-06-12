---
title: "minimal CD installer partitions and boot loader."
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by vikjon0 on 2009-08-19
I am now using the minimal CD and I have some problems with both the boot loader and the partitioner when I am installing on a USB stick with the fixed HD still connected.

1) Partitioner
The paritioner picks up the swap partition on the fixed HD. 
The only way to deselect it is to edit that partition and remove the use as swap. In the next step I am told he is writing a change to the swap on the fixed HD. Pretty annoying. Where is this written? It is pretty critical that nothing is written on the wrong disk! I think this is not a real problem because the swap still seem to exist in the pre-existing system. 

Can anyone confirm that nothing is written on the fixed HD in this scenario? I guessing fstab on the target disk?

2) How do I know which disk is HD0 and resp. HD1 when I have to decide where to write the boot loader? Is the order they are presented in the partitioner?

3) I managed to pick the correct HD. How can I get the boatloader to ignore OS on the other disk?
Now I get the selection screen on BOOT and if I select the OS on the fixed disk it is not found. The not found part is probably becsause I changed the boot order...

Would be nice if you could tell the installer to ignore other disks all together....

---

### Post by mikewhatever on 2009-08-23
> **vikjon0 said:**
> ....
1) Partitioner
The paritioner picks up the swap partition on the fixed HD. 
The only way to deselect it is to edit that partition and remove the use as swap. In the next step I am told he is writing a change to the swap on the fixed HD. Pretty annoying. Where is this written? It is pretty critical that nothing is written on the wrong disk! I think this is not a real problem because the swap still seem to exist in the pre-existing system. 

Can anyone confirm that nothing is written on the fixed HD in this scenario? I guessing fstab on the target disk?

Can you quote the exact message, or else explain how you know changes are written to the wrong disk. I think telling the installer not to use a partition as swap makes perfect sense.

> 2) How do I know which disk is HD0 and resp. HD1 when I have to decide where to write the boot loader? Is the order they are presented in the partitioner?

One way is to look at their respective partition layouts.

> 3) I managed to pick the correct HD. How can I get the boatloader to ignore OS on the other disk?
Now I get the selection screen on BOOT and if I select the OS on the fixed disk it is not found. The not found part is probably becsause I changed the boot order...

Would be nice if you could tell the installer to ignore other disks all together....

You need to edit GRUB's menu, /boot/grub/menu.lst, and remove the OS entry you don't want.

---

### Post by vikjon0 on 2009-08-24
Thank you for your answers!
[PHP]
Can you quote the exact message, or else explain how you know changes are written to the wrong disk. I think telling the installer not to use a partition as swap makes perfect sense.[/PHP]
I am pretty sure that the result was correct and maybe it makes sense. My concern is the screen where you see which partitions that will be changed. Not using a partition from the fixed disk as swap is seen as a change. My worry is that I do not want to touch the fixed disk. I understand now (?) that this particular change is REGARDING that partition not ON/IN it. Since some changes could include wiping the partition and other just an entry in fstab on a different disk, it did not look good to me. Maybe if I read more carefully it would have been clear to me. 

> One way is to look at their respective partition layouts.
I think I get what you mean. I also see on the desktop installation that you can use the sda/b code instead. 

> You need to edit GRUB's menu, /boot/grub/menu.lst, and remove the OS entry you don't want.
Yes, this was the smallest problem. But I think a difference compared to the desktop installation is that if there is no other OS found or at least if there is only one disk you don't get the question if write bootloader or not.
I guess export mode is the answer to that.

---

