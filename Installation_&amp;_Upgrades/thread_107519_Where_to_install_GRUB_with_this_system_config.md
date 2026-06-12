---
title: "Where to install GRUB with this system config?"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by rafaelperrone on 2005-12-23
Im new to Linux and I know I did lots of mistakes, please help me.

Im installing Ubuntu on a system with the folowing config:

1 - 80 GB SATA drive with Win XP
2 - 160 GB SATA drive with Kubuntu
3 - 40 GB IDE drive with lots of MP3 and no OS

When the installation asked me where to place GRUB I chose default option, which is first hard drive. I was expecting for it to insall on my first SATA drive, which is the WinXP one. But it installed on the first IDE drive.

I dont want to boot from the IDE drive. So I installed again and this time I chose for it to install grub on the /dev/sda (which I believe to be my first SATA drive, correct me if Im wrong). But the I could boot from any of my disks, not even WinXP. When It would load during boot GRUB my screen was filled with GRUBS and it never stops.

So I did a fixboot and fixmbr to the windows drive and windows is working again. But not my Kubuntu install.


How can I place grub on any of my WinXP SATA drive (I think my bios wont let me boot from the other SATA drive, as I can just choose "SCSI" from the boot options and not "SCSI1" or "SCSI2" or "SATA1", or ...whatever, just "SCSI") and get it to work properly?

WHats your advice on where to place GRUB? DO you think I should place it on which drive?

Thanks a lot!

Rafael

---

### Post by localzuk on 2005-12-23
Why can you not use the IDE drive as the boot device? It would save a lot (imo) of hassle. All you need to do is have it set as the primary boot device in the bios and install grub onto it. Then on booting it will 'boot' from that device - just showing the grub loader.

---

### Post by rafaelperrone on 2005-12-23
Because I use the IDE drive only for MP3s and sometimes I take it out of the computer to copy some more mp3 at come friends' computer. So, if I did that my computer wont boot any more.

Any other ideas?

---

