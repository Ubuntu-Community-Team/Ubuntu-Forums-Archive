---
title: "Computer stoped recognizing CDroms"
date: 2016-01-13
forum: Hardware
---

### Post by Callmestupid on 2016-01-13
I have been using Ubuntu 14.04 LTS since it came out without problems until recently. I can not open either DVDrom drive. They do not show up on available drives listing I looked in the /cdrom dir and there is nothing there no files nothing. I don't remember what I typed but I did find that they are in a listing as ata-atap_dvd_a_DH20A4P with a sr0 a line or two below it ans ata-LITE-ON_DVDRW_LH20A1P with an sr1 a line or two below. I need to use the drives I've tryed to find threads but nothing seems to work and Im at witts end.

Thank you

---

### Post by Autodave on 2016-01-14
When you try either drive by putting a disc into them, does the icon appear on your desktop telling you that the machine at least recognizes that the drive has a disk in it?

---

### Post by Callmestupid on 2016-01-14
No I can not open the drives at all from inside or outside of the computer.

---

### Post by Callmestupid on 2016-01-15
Even the poke hole won't open the drive the second drive does not have a poke hole.

Here is a copy of my fstab filemount
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=6facc9ee-f062-4070-984e-c7ae53c53844 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3c9c48f2-fad5-4b38-92d7-bca40ef40180 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=82db6f04-4e89-4b018ae7-b01f988f9625 /                ext3

---

### Post by Callmestupid on 2016-01-15
Here is result of blkid:

/dev/sdb1: LABEL="Spare" UUID="3c90f083-668c-40be-afea-5083779b73db" TYPE="ext4" 
/dev/sdb5: LABEL="Mythbuntu" UUID="5cc811de-ca89-44ed-a6f7-0f1429c7a49a" TYPE="ext4" 
/dev/sdb6: UUID="67f5991d-bbea-455d-8b1a-d55bc6faabf5" TYPE="swap" 
/dev/sdc1: LABEL="Data01" UUID="6facc9ee-f062-4070-984e-c7ae53c53844" TYPE="ext4" 
/dev/sdc5: UUID="3c9c48f2-fad5-4b38-92d7-bca40ef40180" TYPE="swap" 
/dev/sdd1: UUID="CA5C671C5C670315" TYPE="ntfs" 
/dev/sdd2: LABEL="Recovery" UUID="2C88743C8874071C" TYPE="ntfs" 
/dev/sde2: LABEL="Christian Music" UUID="7420AA793341732B" TYPE="ntfs" 
/dev/sde3: UUID="485a9bed-9eb3-445f-b556-d0e33fc835ce" TYPE="swap"

---

### Post by yancek on 2016-01-15
Do you see a new entry when you are in the /media/username directory and you insert a DVD?

---

### Post by Callmestupid on 2016-01-15
I can not open the drives therefore I can not insert a disk.

---

### Post by Autodave on 2016-01-16
Sounds like a hardware problem: not a Linux problem.  Possible power supply failure, loose connection from power supply to CDs, or both CDs crapped out at the same time?  Kinda weird that fstab knows what is in them: that tells me that they are at least spinning and reading.

If it were me, I would pull cover and check connectors: sometimes the simplest thing of removing connectors and reinstalling them will take care of poor or loose connections.

---

### Post by Callmestupid on 2016-01-16
Both the power lights on both drives come on and they seem to attempt to open when the eject button on the front of each drive is pushed. Will check the connections in the AM. Thanks

---

### Post by Autodave on 2016-01-17
If the power lights are both working, and Linux is reading what disc is in both drives, then it sounds to me like both CD bit the dust at the same time or else something is jammed inside of them. Could anybody have gotten to the machine when you weren't around and stuck something inside the drives?

If connections check out OK, you are probably going to have to remove the drives and disassemble them: at least if you want your discs back.

The puzzling thing here is that you cannot open the one drive that has the access hole in it............ You may want to try the pokehole with the computer shut down.

---

### Post by Callmestupid on 2016-01-19
All the cables were fit correctly. removed both drives and replaced one with a spare I had on hand. It works!!!! I checked both drives were empty.Thanks for the help. callmestupid
Not sure how to close the thread but it can be closed.

---

