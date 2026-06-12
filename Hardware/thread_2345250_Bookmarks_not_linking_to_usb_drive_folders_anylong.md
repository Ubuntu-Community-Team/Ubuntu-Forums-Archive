---
title: "Bookmarks not linking to usb drive folders anylonger"
date: 2016-12-02
forum: Hardware
---

### Post by xinuzi on 2016-12-02
The subject will possibly have been mentioned here before, but still...

Case on my Ubuntu 16.04 X64:

The bookmarks that I had set to certain folders on my external usb ntfs drive suddenly didn't work anylonger.

In Nautilus (Computer)/media/me my usb drive showed as: 

- Drive (the name of my drive) <- disactivated
- Drive1 <- disactivated
- Drive 2 <- active

As the bookmarks referred to the active 'Drive' before they didn't work anymore as 'Drive' had become 'Drive2' automatically.

Everytime I plugged the drive in and out the situation stayed the same.

Solution: 

- Right click in folder /media/me and 'open in terminal'.
- Command: 'sudo rmdir Drive' and 'sudo rmdir Drive1'.

After that 'Remove Safely' the drive.
Replugin.

Everything restored. 
/media/me displays active 'Drive' only.

Experienced users may find sth like this very logical and super simple, but I think beginners 
could struggle with their automatically mounted external usb drive being automatically renamed and their 
bookmarks not functioning anymore.

Further tips, ideas, comments on this welcome..

---

