---
title: "[SOLVED] ahci adding 30-seconds to startup?"
date: 2008-07-11
forum: General Help
---

### Post by moore.bryan on 2008-07-11
hopefully someone has a solution for this little issue of mine...
boot-up hangs for about 30-seconds at the following text during startup:
```
Jul 11 09:18:07 thinkpad kernel: [   14.174626] ahci 0000:00:1f.2: nr_ports (4) and implemented port map (0x1) don't match, using nr_ports
Jul 11 09:18:07 thinkpad kernel: [   14.174708] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0xf

```i've searched google and other threads, but nothing seems to work short of adding "acpi=off" to my grub kernel line and that is NOT an option since i'm on a laptop.

thanks, in-advance.
=====
EDIT 1:
okay, to add a little more info... i found through self-discovery ahci issues are occasionally related to bios issues, so i went into bios and changed my sata choice from "ahci" to "compatibility." now, the wait doesn't occur as above; rather, it waits here:
```
Jul 13 14:39:41 thinkpad kernel: [   24.320919] ata1.00: configured for UDMA/100
Jul 13 14:39:41 thinkpad kernel: [   24.640481] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, 1.02, max UDMA/33

```hopefully, this extra info will allow SOMEBODY to give me a suggestion or two...
;-)
=====
EDIT 2:
so, i've updated the bios to the latest version, changed the sata choice back to "ahci" and now the lag is only ~10-seconds; still irritating, but not nearly as bad as before. the hang still occurs at the "ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, 1.02, max UDMA/33" line. still awaiting any ideas!
=====
EDIT 3:
okay, you can almost disregard the above... sometimes boot still hangs at the ahci nr_ports thing, still for 30-seconds, and other times it hangs as the ATAPI DVD thing, for about 10-seconds. what gives!? please, someone...ANYONE... suggestions?
=====
EDIT 4:
okay, this should be my final edit, as i SEEM to have solved the issue. for anyone else having this issue, the following steps MIGHT work for you too...

[LIST=1]
[*]edit /etc/initramfs-tools/modules and write-in a specific order of modules to load at boot:```
sudo nano /etc/initramfs-tools/modules
``` and add ```
ahci
ata_piix
```
[*]update initramfs:
```
sudo update-initramfs -k all -u
```
[*]reboot and see...
[/LIST]

---

### Post by kozimodo on 2008-07-31
Thanks, that did the trick for me too!

---

### Post by moore.bryan on 2008-08-01
excellent... glad to hear it wasn't unique to me!

---

