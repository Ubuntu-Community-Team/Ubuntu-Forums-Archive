---
title: "GA-EP35-DS3L- Grub doesn't work......"
date: 2012-08-31
forum: Hardware
---

### Post by leezer3 on 2012-08-31
OK, so I'm looking for anyone with any experience in this please, as I've tried *everything*.
In short, the S939 board in my server decided to die. To this end, I acquired a GA-EP35-DS3L (v1.0) and stuck in a spare 775 chip. From there, nothing's worked.

This is what I've tried so far:
1. Original install was Grub legacy, everything OS related living on a single IDE drive. (First in the boot order)
2. Plugged in all drives and turned on- Grub error 21. Fair enough, I loaded up Grub rescue disk, and attempted to reinstall; Drive numbers change.....
3. Grub rescue can find no trace of my disks, and keeps complaining of invalid partition tables.
4. Mildly annoyed, load up SuperGrub2 to install Grub2- Doesn't like the drives either.
5. Decide to do a reinstall with Ubuntu. This finds all drives and partitions exactly where they're supposed to be- Sucess?
No, all appears well until reboot, when I get a UUID not found error.
6. Reboot into Ubuntu rescue, and attempt a manual bootloader install. The kernel sees all the drives just fine again, but attempting a manual Grub install shows it can't actually find the drives properly. All it gives is "error physical volume pv0 not found" errors.

I've also tried Lilo and a complete reinstall of Grub Legacy (Both via a Mandriva netinstall/ rescue disk), but no dice there.

From what I can find, this board is using a Jmicron IDE controller, which I suspect is at the root of all my problems :(
Still doesn't explain why Grub doesn't see the SATA drives though.

Does anyone have any clever ideas please?- I'm utterly stumped.

---

