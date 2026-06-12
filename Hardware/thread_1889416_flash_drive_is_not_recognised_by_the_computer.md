---
title: "flash drive is not recognised by the computer"
date: 2011-12-01
forum: Hardware
---

### Post by tediuskalangwa on 2011-12-01
Hi everyone,

I wanted to format the flash drive,I clicked on format after few minutes I canceled.Since then if insert the flash it is not seen,what could be the problem please help

---

### Post by ajgreeny on 2011-12-01
If you cancelled while the format was happening, you probably have a corrupt partition table.

I suggest you use gparted, and click on the Device menu and choose "Create partition table" use the ms-dos option that comes up (the default), and after that you should be able to make a new partition on the drive.

Just make sure you do all this to the correct drive or you could wipe your hard disk installation.

---

### Post by tediuskalangwa on 2011-12-02
what settings should i focus on when making new partition on the drive.Please help me am new in ubuntu

Thanks 
Tedius

---

### Post by pqwoerituytrueiwoq on 2011-12-02
for a flash drive use fat32 and use the max size if the driver is over 32gb use a ntfs system
use ext2 if you don't want windows using the drive (without 3ed party software)

---

