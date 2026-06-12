---
title: "Nautilus opens removable media on resume from sleep"
date: 2009-04-05
forum: Hardware
---

### Post by lanteau on 2009-04-05
On my laptop I use a 16GB SDHC card in the laptops built in reader for additional storage. Whenever I resume from putting the laptop in sleep, it opens a nautilus window to the removable card. How do I stop it from automatically opening this window on resume? Thanks

---

### Post by mtbsoft on 2009-04-05
In Nautilus, use Edit | Preferences to display the File Management Preferences dialog.  Go to the  Media tab and clear (un-tick) the *Browse media when inserted* option.

When you resume the computer, the SD card is remounted which causes it to re-browse the media.  Changing this option does mean you won't get a browse window displayed any time you insert a card as well, though - personally I found this annoying so don't mind.

---

### Post by lanteau on 2009-04-08
Thanks a lot this worked. I swear that I tried this before and it still was doing it but when I went to that Media tab again it was still checked, so somehow it didn't save the setting when I unchecked it before and thats why I thought that didn't fix it. So now it behaves how I like, thank you.

---

### Post by reesje on 2009-11-18
> **mtbsoft said:**
> In Nautilus, use Edit | Preferences to display the File Management Preferences dialog.  Go to the  Media tab and clear (un-tick) the *Browse media when inserted* option.

When you resume the computer, the SD card is remounted which causes it to re-browse the media.  Changing this option does mean you won't get a browse window displayed any time you insert a card as well, though - personally I found this annoying so don't mind.
I guess this is a workaround rather than a solution.

Does anybody have a solution that does not stop nautilus from opening when a card is inserted, but prevents nautilus from opening when the PC is brought out of standby?

Thanks in advance.

BR,
René

---

