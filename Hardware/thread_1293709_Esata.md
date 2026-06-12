---
title: "Esata"
date: 2009-10-17
forum: Hardware
---

### Post by Asheguy79 on 2009-10-17
Dose Ubuntu 9.04 support E-SATA?  If so how do I need to do anything special to set it up or is it just ready to go.  I am also having trouble setting up a RAID 5.  Everytime I try I end up with LVM's and I am setting up a LAMP server and I think the RAID 5 will work the best for this, am I right?  If so how can I set up a RAID 5?  I am using the taskel desktop edition of LAMP to set up the server, still need the desktop as this is my only computer.

---

### Post by paulisdead on 2009-10-17
Are you using a hardware RAID controller, software RAID, or motherboard fakeraid?

For software you need the alternate install disk if you're doing a clean install, otherwise, just google around for an mdadm how to and you can add the array to an existing server.

Unless you're dual booting windows, don't bother with motherboard fakeraid, and just do software.

If it's a real hardware controller, the alternate install CD should hopefully have the driver for it.

You haven't stated exactly what you're doing with the system, and the hardware involved, so I can't say if RAID5 is right for it or not.  RAID5's write performance is pretty lousy, so if you plan on using a database that will be heavily written to, RAID10 might be better, but you lose more space.  I also wouldn't do RAID5 if you have a lot of large disks.  I think it was around every 12-14TBs that disk manufacturers expect a bad sector to occur, and if that happens to be on your parity data during a rebuild after another drive has failed, you could be screwed.  There's still a chance of it happening with smaller arrays, as well, so it's not that safe of an option.  RAID6 takes up 2 drives worth for parity, but just pushes the problem out further.

*edit* oh ya, if for the esata, if it's an intel disk controller, you need to make sure ahci is enabled in the bios if you want hot plugging to work.  I'm not sure of the status of hot plug on other controllers right now.

---

