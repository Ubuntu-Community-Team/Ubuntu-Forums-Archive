---
title: "usb hard drive, how to delete files?"
date: 2011-07-18
forum: Hardware
---

### Post by ubto66 on 2011-07-18
ubuntu 10.04
usb hard drive.

If I delete a file on the usb hard drive by using 'move to trash',
the file is moved to the trash-folder.

Is there a way to delete files/folders on an usb hard drive, and the
deleted files/folders are not moved anywhere, just deleted?

Thanks.

---

### Post by TheMatej on 2011-07-18
you can do this from terminal:
```
rm *filename *or rm -R *dirname*
```
or you simply drag file to trash while holding button *shift*

MK

---

### Post by coffeecat on 2011-07-18
> **TheMatej said:**
> or you simply drag file to trash while holding button *shift*


... or, similarly, highlight file and shift+delete keys.

---

### Post by ubto66 on 2011-07-18
Thanks for answering.
I tried the rm in terminal, and it seemed to work.
Pressing shift, and dragging the file to the trash didn't work.
The files appeared in trash, and know they can't be deleted/removed from
trash. So how do I clear the trash?

---

### Post by Cybie257 on 2011-07-18
My preferred method is to go to the nautilus preferences.

Edit -> Preferences -> Behavior(tab)

Than select (Trash)-Include a Delete command that bypasses trash.

When you select file(s) that you want to delete, just right-click and select 'Delete'...

Makes a simple one-step process that doesn't require holding shift or typing anything. 

-Cybie

---

### Post by roololing on 2011-07-18
Right-clicking the Trash icon in the launcher should show an option to "Empty Trash," which deletes everything in the Trash.

---

### Post by ubto66 on 2011-07-25
Thank you for your answers.
After restarting the files in the trash bin were removed.
To remove files I will use terminal and rm command.

---

