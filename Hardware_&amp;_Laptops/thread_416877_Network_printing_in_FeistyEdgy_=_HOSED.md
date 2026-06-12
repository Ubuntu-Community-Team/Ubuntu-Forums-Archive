---
title: "Network printing in Feisty/Edgy = HOSED?"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by jmagsho on 2007-04-21
I've got an HP Photosmart 3210 multifunction printer that is giving me fits.   It worked just fine under Breezy and Dapper.   Once I upgraded to Edgy and now to Feisty, it's been a complete horror show.   It seems that CUPS is just totally hosed.   

I had it working last night and once I bounced my machine it's back to being hosed.    It's now got me seriously considering going back to Fedora which is really a bad thing. :( 

All I can get the foolish thing to print is an error dump page.   It looks like the rights/permissions for CUPS somehow got hosed in the newer versions based on the debug log from CUPS.

I'm getting a 'no bounding box error' 

Anyone have any insight?  I've tried all the suggestions I could find in the forums thus far...

---

### Post by Syke on 2007-04-21
Hang in there, I've got the same printer and don't have any problems with it, so it's probably a fixable problem.

---

### Post by jmagsho on 2007-04-21
Syke,

What driver are you using, HPLIP or HPOJ?

---

### Post by Syke on 2007-04-22
I'm using the hpijs driver for the 3200 series, and the printer is a network printer, using HP JetDirect to a static IP. IIRC, these drivers worked out of the box in Edgy. I just added the printer using the New Printer wizard.

---

### Post by jmagsho on 2007-04-23
I think I figured this out.  I added my user to the shadow group and then installed 'hpoj' which seems to have gotten this working again using the JetDirect setup.

Thanks for your help Syke.

---

