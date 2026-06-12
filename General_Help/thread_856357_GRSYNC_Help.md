---
title: "GRSYNC Help"
date: 2008-07-11
forum: General Help
---

### Post by strange_cathect on 2008-07-11
Hello,

I'm using the GRSYNC GUI to do some backups of important folders with rsync. But I'm having an issue where whole folders or files will not make it from the source to the destination. 

I'm sure I need to just click the correct settings. Could someone help me with this? 

In my screenshot (attached) I am trying to back up a SOURCE folder on my desktop (which contains several other folders) to a DESTINATION USB drive. 

With my current settings (see screenshot) whole folders are not sent to the DESTINATION and many files do not get updated.  Help!

---

### Post by silkstone on 2008-07-11
Try unchecking 'Preserve Owner' and 'Preserve Permissions'.

Also make sure that all the Advanced Options are unchecked.

That will put your configuration the same as mine, and I haven't had a problem. Let's know if it works.

---

### Post by timcredible on 2008-07-11
> **silkstone said:**
> Try unchecking 'Preserve Owner' and 'Preserve Permissions'..

only do this if you don't want to put the files back.

can you post your mounted filesystems, sounds like maybe the usb drive isn't mouting where you think.  also, are you sure about the space in the volume label?  i'm not sure if that's allowed or not....

---

### Post by silkstone on 2008-07-11
> **timcredible said:**
> only do this if you don't want to put the files back.

I was assuming he was writing to a FAT32 drive, and FAT32 doesn't recognise permissions anyway.

---

