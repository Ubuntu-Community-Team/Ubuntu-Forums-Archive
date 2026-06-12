---
title: "Second Hard Drive Doesn't Show"
date: 2024-08-21
forum: Hardware
---

### Post by daniell59 on 2024-08-21
Please educate me.
I tried 4 different hard drives and they were not detected. They did not show in disks or GParte. This is more for educational purposes than actual need.

Ubuntu 24.04

Thanks

---

### Post by currentshaft on 2024-08-21
it

---

### Post by daniell59 on 2024-08-21
> **currentshaft said:**
> Do you think maybe, just maybe, it might be relevant to share ... oh, I don't know ... the types of drives, what state they're in, how they're connected to the PC, etc?

No offense, but how do you post here for 16 years and not pick up on this obvious requirement to get technical help?

Like, read your post again and try to picture a complete stranger trying to make sense of it. They know even less than you about your hardware. What do you expect them to say or do in response to such a low effort post?

You could have ignored it.

---

### Post by yancek on 2024-08-21
> You could have ignored it. 

Looks like everyone else is but I'll give it a try.  Based on your posts, you apparently know very little about computers so I will ask some very basic questions.  

Are these drives physically attached to the computer?  (Did you check the connections if they are?)
Do you have partitions with filesystems on them on these drives?
If so what filesystem do you have?
Do any of these drives contain another operating system and if so, what is it?
Have you been able to access these drives previously from Ubuntu?

---

### Post by oldfred on 2024-08-21
If 4 drives, I would first check for bad cable or power connection.

---

### Post by daniell59 on 2024-08-21
> **yancek said:**
> Looks like everyone else is but I'll give it a try.  Based on your posts, you apparently know very little about computers so I will ask some very basic questions.  

Are these drives physically attached to the computer?  (Did you check the connections if they are?)
Do you have partitions with filesystems on them on these drives?
If so what filesystem do you have?
Do any of these drives contain another operating system and if so, what is it?
Have you been able to access these drives previously from Ubuntu?

Thanks for your reply. 
I wanted to dual boot Ubuntu and Windows. I need to do a few things on Windows that is difficult in Ubuntu.
I I hooked up an old hard drive with a SATA cable. I tried to install Windows. It would freeze after I hit install. I tried 3 other hard drives with the same result. I thought that I could use disks to see what was going on. They did not show up. I could not find them in the BIOS either.
Though my knowledge is limited, I wanted to try to expand it.

---

### Post by Yellow Pasque on 2024-08-21
> I could not find them in the BIOS either.
Did you try different SATA ports and cables? Do you have one of those motherboards that disables certain SATA ports when certain PCI-e or M.2 slots are used? (consult your motherboard's manual)

---

### Post by daniell59 on 2024-08-21
> **Yellow Pasque said:**
> Did you try different SATA ports and cables? Do you have one of those motherboards that disables certain SATA ports when certain PCI-e or M.2 slots are used? (consult your motherboard's manual)

Tried different SATA cables and ports.
My motherboard is very old. Too old to have M.2 slots
I wanted to install windows for the following reason.
Soon I will build a new computer and I will have to flash the BIOS.

---

### Post by Yellow Pasque on 2024-08-21
If you can't get the drive to show up in the BIOS, there's no "trick" you can do in the OS (Ubuntu, Windows, whatever). There may be settings you have to change in the BIOS (like SATA Controller mode), but since you didn't tell us what model motherboard you have, that's as specific as I can get.
EDIT: These are mechanical hard disks (not solid state), correct? You can hear the motor(s) running, correct?

---

### Post by daniell59 on 2024-08-22
> **Yellow Pasque said:**
> If you can't get the drive to show up in the BIOS, there's no "trick" you can do in the OS (Ubuntu, Windows, whatever). There may be settings you have to change in the BIOS (like SATA Controller mode), but since you didn't tell us what model motherboard you have, that's as specific as I can get.
EDIT: These are mechanical hard disks (not solid state), correct? You can hear the motor(s) running, correct?


Biostar N68SA-M2S
On my last attempt I heard a clicking sound coming from the hard drive.

---

### Post by Yellow Pasque on 2024-08-22
Biostar's manual is lacking with BIOS settings, but in general, make sure the SATA controller is enabled and in AHCI mode. Make sure any RAID or "NV RAID" is disabled.
Hard disks use to have jumpers to force SATA 1.5Gbps modes because some older chipsets wouldn't "autonegotiate" the speed, but I don't think newer 6Gbps disks have jumpers to force 3Gbps mode.

---

### Post by daniell59 on 2024-08-22
> **Yellow Pasque said:**
> Biostar's manual is lacking with BIOS settings, but in general, make sure the SATA controller is enabled and in AHCI mode. Make sure any RAID or "NV RAID" is disabled.
Hard disks use to have jumpers to force SATA 1.5Gbps modes because some older chipsets wouldn't "autonegotiate" the speed, but I don't think newer 6Gbps disks have jumpers to force 3Gbps mode.

Thank you for your informative reply.
Unless I am missing something, there is no AHCI mode in the BIOS.

---

### Post by daniell59 on 2024-08-23
I just solved the problem. In the BIOS I disabled the floppy drive. I don't have one installed. Afterwards the hard drives were detected.

---

### Post by Yellow Pasque on 2024-08-23
That is strange. I don't think I've ever seen the floppy header have any relation to the SATA controller, and I built a decent number of systems back in the days when boards still had floppy headers.

---

### Post by daniell59 on 2024-08-23
> **Yellow Pasque said:**
> That is strange. I don't think I've ever seen the floppy header have any relation to the SATA controller, and I built a decent number of systems back in the days when boards still had floppy headers.
I guess I can enable the floppy and see what happens. That will be for another day.

---

### Post by daniell59 on 2024-08-31
> **Yellow Pasque said:**
> That is strange. I don't think I've ever seen the floppy header have any relation to the SATA controller, and I built a decent number of systems back in the days when boards still had floppy headers.
You were correct. The problem turned out to be a defective SATA Power connector. 
Thank you for your informed and constructive input.

---

