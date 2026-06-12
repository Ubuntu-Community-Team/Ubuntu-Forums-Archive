---
title: "Owner free usb drive"
date: 2008-09-17
forum: General Help
---

### Post by AJB2K3 on 2008-09-17
I sure I just missing something obvious but I have a 160gig drive formatted to ext3 (to hold 4+gig files) but I have to chown the files everytime I connect it to a different pc,
Is there a way to just read and write ext3 from any ubuntu pc?

---

### Post by EmanresuusernamE on 2008-09-17
Put everything in a folder, right-click on that folder, and then switch to the Permissions tab.  Change everything for everyone to Read And Write.

Or use:
chmod 777 <File Name>

---

