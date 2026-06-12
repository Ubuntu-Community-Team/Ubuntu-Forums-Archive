---
title: "SATA Harddrive not seen by Drake"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by vincentbahnan on 2007-04-30
Hi all,

I wish to add a 300GB SATA (SeaGate Barracuda 7200.10) harddrive to my PC running Dapper Drake which currently boots via a 40GB IDE harddrive. The motherboard is a Gigabyte 7VAXP Ultra and the SATA controller is a Silicon Image 3112A (the chip is also embedded into the MOBO). The HD has been set to 1.5GB/s.

The BIOS for the SATA sees the harddrive but once Ubuntu is running, and I go to the Gnome Partition manager, I see the IDE harddrive but not the SATA. There is also no SDA "files" in the /dev directory.

I recently installed some SATA modules but these didn't seem to work. I have considered flashing the BIOS of the MOBO with a more recent version which contains updates to Silicon Image's SATA BIOS because there have been instances when the SATA HD is not seen at all. I am not keen on doing this; however I have already backed up the original BIOS.

I have also unplugged the IDE drive to see if I could install Ubuntu on the SATA HD but the installation CD could not detect the drive. Furthermore, a windows installation CD was also unable to see the HD.

Does anyone know of any procedure to make my SATA HD visible to Ubuntu?

I know there is no problem with the HD itself as I installed Win XP on another PC. Unfortunately, the other PC was only on loan so I no longer have access to it. 

I guess all I require is the SATA drivers which work on Ubuntu Dapper! I have downloaded similar drivers but they are for RedHat and assume that they won't work.

I would appreciate very much assistance in this matter.

With thanks in advance,
Vinnie!

---

