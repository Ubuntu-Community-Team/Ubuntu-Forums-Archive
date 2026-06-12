---
title: "Reinstalling Ubuntu - MBR"
date: 2008-10-26
forum: General Help
---

### Post by slibuntu on 2008-10-26
Heya,


I'm dual booting Vista and Ubuntu. I've messed up an Intrepid beta install, and want to wipe the partition and do a fresh one, but I know that this will feck up the MBR.

If I wipe the partition from Vista, then without rebooting use the fixmbr tool, will that sort it out so I can shut down and pop in a live CD and reinstall?

Thanks people!

---

### Post by TeXtonyx on 2008-10-26
I don't think you can access any boot files while Windows is active.
So I don't think you can use fixmbr and have it stick.
You will need to reboot and use the install cd with bootrec.

I'm assuming that you had 8.10 write to the MBR and that is why
you need to fixmbr.

It is possible in Step 7 under Advanced, to write the grub boot
files to the Ubunut boot partition. Then use Easybcd for Vista
to add Ubuntu to the boot menu. Then if you lose the Ubuntu 
partition, you don't need to fix Windows. If the Windows bootloader
has a problem, you can use Super Grub to boot Ubuntu from its
/boot partition. I think this method is more robust since either
OS can be booted without depending on the well-being of the other OS.

I suppose it can't hurt to try to fixmbr before rebooting to bootrec.
And it may appear to work, but don't be surprised if you need to rerun fixmbr.

---

