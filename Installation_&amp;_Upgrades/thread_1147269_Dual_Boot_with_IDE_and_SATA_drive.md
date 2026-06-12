---
title: "Dual Boot with IDE and SATA drive"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by LonelyTraveler on 2009-05-03
Hi guys and girls.

My friend want to install Ubuntu and Windows, but the one will be on a IDE drive and the other on a SATA drive. Do you know if this is possible? If so, is there any extra configuration required?

Thanks.

---

### Post by Mark Phelps on 2009-05-03
Everyone has their own way of doing this, but I would recommend the following (the way I did it):

Install the two OS's each on their own drive.

Install MS Windows to the SATA drive, Ubuntu to the IDE drive. Depending on the motherboard, you may have difficulty getting MS Windows or Ubuntu to see the SATA drive.  In my experience, it was easier to track down Mobo SATA drivers for MS Windows for my Mobo.

Disconnect the Ubuntu drive, install MS Windows.

Disconnect the MS Windows drive, install Ubuntu on the other.

Reconnect both drives, boot from the Ubuntu drive, add the MS WIndows stanza to the menu.lst file manually.

Done.

Note: Others have done this different ways and will undoubedtly have different suggestions. But this way, I leave each drive's MBR intact -- which helps immesurably when I have to "repair" the MS Windows (Vista and Seven) drive.

---

### Post by LonelyTraveler on 2009-05-13
Thanks Mark. 

My friend is gonna give it a shot.

---

