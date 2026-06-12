---
title: "HP ML310 + Adaptec 1420SA - won't boot"
date: 2010-08-07
forum: Hardware
---

### Post by Lousek on 2010-08-07
Hello Forum

First: Sorry for my bad english ;)

I have here a problem with a HP ProLiant ML310 G1 server. 
I am not sure if this is the right place for the post; please move it to the right location if it is wrong. 

Some specs:
CPU: Intel P4 2.8 GHz
RAM: 512MB
Disk1: 40GB IDE (connected to "Integrated Ultra ATA100 IDE RAID Controller")
Disk2: 160GB IDE (connected to "Integrated Ultra ATA100 IDE RAID Controller")
Disk3: 1TB SATA-II (connected to "Adaptec 1420SA", Legacy mode)
Disk4: 1TB SATA-II (connected to "Adaptec 1420SA", Legacy mode)
PCI-Card1: Adaptec 39160 SCSI-Controller (used for Tape Library)
PCI-Card2: Adaptec 1420SA SATA-II RAID Controller (used for 1TB-drives)

I installed Ubuntu Server 10.04 on the 40GB-drive. The server is used as backup server. 
Now the problem (I am not sure if it is a Linux-problem or not):
I attached the two 1TB-drives to the controller and turn the server on. The BIOS-messages are displayed, but at the point "Booting from Harddisk (Drive C)", the system hangs. 
I read, that the support for the Adaptec 1420SA-Controller is not very well in  Ubuntu / Debian. 
Then, I disconnected the two 1TB-drives from controller and tried again. Success! The system boots. 
I took a look at the driver: sata_mv is used. 
Then I attached the two drives. They were automatically detected. 
I created a new ext4-filesystem on each drive, and copied test data to them. Success!
I also wrote entries to /etc/fstab for this disks (using everywhere the UUIDs). 

Then, I restarted the system (without disconnect the drives from the controller) ... same problem, the system hangs at "Booting from Harrdisk (Drive C)". No failure message. CTRL + ALT + DEL also does nothing. 
The Boot Controller Order is okay (first the IDE- then the SATA-Raid-Controller), also the Boot Order (1. Floppy, 2. CD-Rom, 3. Harddisk, 4. NIC). 

Does anyone have an idea what the problem could be?

Best regards and many thanks,
Lousek

---

### Post by Fafler on 2010-08-07
I think BIOS still tries to boot from the wrong drive. Or maybe GRUB tries to detect OS'es on the other drives, but is unable to do so. Can you disable the BIOS on the Adaptec controller?

---

### Post by Lousek on 2010-08-07
Hello Fafler

Yes, I thought the same ... I put an PCI-IDE-Controller into PCI-Slot1 (the SATA-Controller is in Slot 2) and connected the system-drive (40GB) to the additional Controller. 

Now it is running ... seems to be a problem of the server itselfs. 

BR,
Lousek

---

