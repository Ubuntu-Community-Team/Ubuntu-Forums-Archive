---
title: "cdrom eject key does not work-Acer TimelineX"
date: 2010-11-14
forum: Hardware
---

### Post by jlh68 on 2010-11-14
With Ubuntu 10.10 on my Acer Aspire TimelineX 4820T does not work.  It does work with W7.  This is one of two not standard button on this laptop.  The other is a "P" key which under W7 is used to launch applications (or to manage power depending on model).  

On this Ubuntu unit neither buttons have any use.  I have tried to use the keyboard short cuts to program the eject key but it does not respond.

Anyone have any ideas on a solution?

Oh I have made a custom launcher to use to open the cdrom drawer, and the eject with in an application will open it.

---

### Post by Foxcow on 2010-11-15
> **jlh68 said:**
> With Ubuntu 10.10 on my Acer Aspire TimelineX 4820T does not work.  It does work with W7.  This is one of two not standard button on this laptop.  The other is a "P" key which under W7 is used to launch applications (or to manage power depending on model).  

On this Ubuntu unit neither buttons have any use.  I have tried to use the keyboard short cuts to program the eject key but it does not respond.

Anyone have any ideas on a solution?

Oh I have made a custom launcher to use to open the cdrom drawer, and the eject with in an application will open it.



That is odd.  The buttons all worked out of the box for me.  Are you using 32 or 64 bit?  Would you consider re-formatting and installing again?

---

### Post by jlh68 on 2010-11-15
I am using 64-bit.  The eject key is a stand alone key on the bezel around the keyboard.  I think it is not addressed (mapped) by the keyboard set up.  There is also a "P" key with an LED that is beside it and it does nothing in Ubuntu. All the other cdlrom/dvdrom drives have had a button on the door.

---

### Post by Foxcow on 2010-11-15
We have the exact same setup but I wonder what the difference is.


edit:  actually, I just flashed to the most recent BIOS version so that could have made the difference.

---

### Post by jlh68 on 2010-11-16
What BIOS version did you flash?  I have ver 1.15 and I see that Acer has ver 1.19 as the latest.  Also how did you flash it?  I did it once on my netbook but don't remember how to do it.

---

### Post by Foxcow on 2010-11-16
> **jlh68 said:**
> What BIOS version did you flash?  I have ver 1.15 and I see that Acer has ver 1.19 as the latest.  Also how did you flash it?  I did it once on my netbook but don't remember how to do it.


I have the latest version and I flashed from Windows with the executable file.  I believe the instructions that came with the flash say that you can use a usb floppy or usb flash drive to do it as well.



edit:  I forgot to mention that I did a ton of reading on the 4820T and it turns out that the latest BIOS version fixes a slew of problems that people were having.  A lot of people are satisfied with the fixes.

---

### Post by jlh68 on 2010-11-17
I followed **Foxcow**'s advice and updated my BIOS.  I went to version 1.19 which is the latest Acer BIOS for the TimelineX.  It corrected the eject button operation, it made the battery state available.  The kernal does not support the battery statics.  I am not sure what else the newer BIOS version has corrected, but I guess I may never know.

Since I have a dual boot laptop (W7 and Ubuntu 10.10), it was easy to upgrade the BIOS.

Thanks **Foxcow** for your help.

---

### Post by Panacco on 2011-05-14
> **jlh68 said:**
> I followed **Foxcow**'s advice and updated my BIOS.  I went to version 1.19 which is the latest Acer BIOS for the TimelineX.  It corrected the eject button operation, it made the battery state available.  The kernal does not support the battery statics.  I am not sure what else the newer BIOS version has corrected, but I guess I may never know.

Since I have a dual boot laptop (W7 and Ubuntu 10.10), it was easy to upgrade the BIOS.

Thanks **Foxcow** for your help.

Can't seem to find this guide, can you link? Thanks in advance

---

### Post by Foxcow on 2011-05-14
> **Panacco said:**
> Can't seem to find this guide, can you link? Thanks in advance



Are you looking for a guide to update your BIOS?

---

### Post by Panacco on 2011-05-14
Yeah

---

### Post by Foxcow on 2011-05-14
If you dual boot Windows, you can flash in Windows.  Otherwise, use this guide:

[http://ubuntuforums.org/showpost.php?p=10099676&postcount=223](http://ubuntuforums.org/showpost.php?p=10099676&postcount=223)

It worked beautifully for me.

---

