---
title: "Install halts at (initramfs) prompt"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by canoetripper on 2008-12-07
I'm trying to install Ubuntu 8.10 on a new barebones system with an AMD Sempron 3300 processor and 2GB RAM. Following is my journey to-date.

[LIST]
[*]I booted with a Windows Vista HD, just to ensure all was working.
[*]I swapped it with a blank SATA drive, tried to install Ubuntu, and it halted at the initramfs prompt, after what appears to be a series of I/O attempts with the HD (judging by the HD LED).
[*]I then swapped-in a blank EIDE drive, with the same result.
[*]The SATA drive was initially FAT32. I changed it, and both drives are now NTFS (and still don't work).
[*]I have used the same CD to successfully install Ubuntu onto 4 old Dell machines at work. But just to be safe, I also re-burned the iso (still with the same result).
[/LIST]

The error reads:

[COLOR="Green"]Loading, please wait...
BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs)[/COLOR]

I found a thread that suggested replacing "quit splash" with "all_generic_ide", which I did using the F6 option on the initial install options page.  I was then able to view a bunch of error dumps similar to the following, after shich it still halted with the errir described above:

[COLOR="green"][105.564751] sr 0:0:1:0: [sr1] Result:hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[105.564869] sr 0:0:1:0: [sr1] Sense Key : Hardware Error [current]
[105.565062] sr 0:0:1:0 [sr1] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[105.565224] end_request : I/O error, dev sr1, sector 128[/COLOR]

I'm a Ubuntu newbie, so any help is most welcome. Thanks!

---

