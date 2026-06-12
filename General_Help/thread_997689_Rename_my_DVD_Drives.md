---
title: "Rename my DVD Drives"
date: 2008-11-30
forum: General Help
---

### Post by dubrict on 2008-11-30
I have 2 identical DVD drives in my computer, and when I click on an iso to burn it to a DVD, the gnome dialog comes up asking me which drive to write to.  The popup menu where I choose the drive has 2 identical selections.  How do I change the names to be something like "Top Drive" and "Bottom Drive?"
Thanks

---

### Post by mc4man on 2008-11-30
I don't think that's possible unless you had a **correct firmware** for the drive that gave it a different product/model name.

For instance several years ago I bought a sony dvd drive that was actually a rebranded BenQ 1640. It used to show as a sony blah, blah.

After flashing the drive with BenQ's firmware for the 1640 it is now seen as this

> description: DVD writer
       product: DVD DD DW1640
       vendor: BENQ


This is only possible in few cases where you have a rebranded drive and a correct firmware available for it.

Strongly note that flashing a drive with **incorrect firmware** or in the **wrong manner** will ruin the drive forever.
Additionally in the example of my BenQ the warranty was nullified the sec. I flashed it.

Maybe when your drives are listed one is always before the other?

---

### Post by dubrict on 2008-11-30
So nautilus-cd-burner gets the drive names from the firmware?  That's just silly.
I'm about to download the source code and start making some changes.

Thanks

---

