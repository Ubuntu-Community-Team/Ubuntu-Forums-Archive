---
title: "Cloned drive - 'attempting boot from hard drive'"
date: 2016-11-14
forum: Hardware
---

### Post by a1074938 on 2016-11-14
[COLOR=#070F14][FONT=Verdana]Hi All,[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]Apologies if this has been asked elsewhere but I cant find any obvious answers. [/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]I have cloned an installation of Ubuntu from one SATA3 to another SATA3 and tested that both of them work and are functional in the original system. I am unable to run either the original or clone on the target workstation which only has SATA2 connectivity. I need to use this specific workstation as it has 96GB [/FONT][/COLOR][COLOR=#070F14][FONT=Verdana][COLOR=#009900]_RAM_[/COLOR][/FONT][/COLOR][COLOR=#070F14][FONT=Verdana] rather than 8GB.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]Is anyone aware of the reason? is there a difference in them viewing partition/OS installation between SATA2 and SATA3?[/FONT][/COLOR]

[FONT=Verdana][COLOR=#070f14]I can see the drive in BIOS, set it to primary boot and get black screen which hangs on 'attempting boot from hard drive'

The BIOS on the target hard drive with the cloned hard drive installed has a UUID which is different to the original when checking blkid. Do they need to match?[/COLOR][/FONT]

---

### Post by oldfred on 2016-11-14
A true clone should be a bit for bit match or UUID also should match.
And then clone drive cannot be booted in same system as original as then you have duplicates.

Grub, fstab and a few other places have UUIDs in configurations. UUIDs then must match configuration files & partition.

But different hardware may also need different drivers, usually issues are video or Internet hardware related. Best to make sure original system is not using any proprietary drivers.

I only have flash drives, but have found my USB3 flash drives work better on USB2 ports. I would expect SATA3 to also be backwards compativle, but not as fast on SATA2. But some have reported issues with specific hardware.

What else is different in hardware between the two systems?

---

### Post by a1074938 on 2016-11-14
Original system was a quad core intel I7 with 8GB RAM new system has 2 x Xenon 6 core processors with 96GB RAM. 

If I boot into the Ubuntu installer from USB I am able to see the SATA and format/install this installation is then functional.

---

### Post by oldfred on 2016-11-14
So you can install Ubuntu on Xenon system?

I would then just copy whatever else you need rather than clone.
Most configurations are in /home, some system wide in /etc but they may be hardware related and need not to be the same.
If server you also my have more programs & configurations in /etc.

---

