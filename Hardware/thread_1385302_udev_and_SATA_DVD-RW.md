---
title: "udev and SATA DVD-RW"
date: 2010-01-19
forum: Hardware
---

### Post by Bumbler on 2010-01-19
There are several bug reports, from several different distributions, which track the problem with burning CDs and DVDs, particularly from ISO images. Somewhere in the process, something interrupts -- apparently udev -- and spoils the thing.

I've read through all I can find on this, and most of the bug reports remain open. Apparently there is no solution I can find, except to suggest it's a regression on the kernel 2.6.31. Supposedly it was fixed in the latest update (2.6.31-17) but I'm not the only one still having trouble. Simply killing udev doesn't work on my system.

I do manage to get some good burns by using K3B on my Karmic system. It worked that way when I was running openSUSE 11.2; Brasero and other GNOME tools made coasters, while K3B worked most of the time.

Still, in some cases I get an error from K3B verifying the burn, and it indeed does not seem to work when I try to use the disk. Has anyone gotten a handle on this yet?

I'm running Ubuntu Karmic 64-bit on a Dell 545 MT. This affects both the IDE mode (piix) driver and RAID mode (ahci) driver. The primary indicator from the logs is this tail on dmesg:

> [  362.094030] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  362.094038] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  362.094046] Info fld=0x0
[  362.094048] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  362.094055] end_request: I/O error, dev sr0, sector 0
[  362.094062] Buffer I/O error on device sr0, logical block 0


---

### Post by johnnie69 on 2010-02-26
This is a very serious issue, 6 years using Ubuntu now, definately the worst problem ever. Tried different programs, media, changed dvd writer and still getting errors and now burning successfuly but burned media are unreadable/unmountable.

---

### Post by Bumbler on 2010-02-26
My previous attempt to reply was wiped by the forum software. Perhaps I can reconstruct what I wrote.

I'm not the only one researching this issue. Consensus seems to say it's related to the fork which took place in the upstream cdrtools sometime back. Now there is a move to return to the original, and it appears to be resolving most of the issues related to this. For example, on this particular machine, openSUSE 11.2 burns fine, but they switched back to the old cdrtools sources.

It seems to affect almost any SATA burner, seems confined to Intel chipsets and 64-bit. But since SUSE exhibited major issues of another sort, I gave up. I restored the Dell to it's original Vista and I'm using another system for Linux.

---

### Post by johnnie69 on 2010-02-28
Back to Jaunty and the dvd writer works... Now I just have to wait for the new ubuntu release, I guess like everybody else who faces this problem with karmic...

---

