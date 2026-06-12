---
title: "OCZ SSD failure?"
date: 2010-07-06
forum: Hardware
---

### Post by MountainX on 2010-07-06
I'm seeing a bunch of entries like this in my kernel.log. What do they mean?

[26033.842861] ata5.00: error: { UNC ABRT }
[26033.902762] end_request: I/O error, dev sda, sector 7098112
[26033.905365] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[26033.905372] ata5.00: failed command: READ DMA
[26033.905383] ata5.00: status: { DRDY ERR }
[26033.905385] ata5.00: error: { UNC ABRT }
[26033.962835] ata5.00: failed command: READ DMA

Here was the ridiculous reply from OCZ to my trouble ticket:

> Description: OCZSSD2-1VTX30G
-------------------------------------------------------
Comment: you will need to contact the os manufaturer to find out what all that means in your kernel
-------------------------------------------------------
Status changed by: Bryan Kiefer

---

### Post by MountainX on 2010-11-02
I've been using the drive. It's fine. Not sure what caused the error messages, but apparently it was transient.

---

