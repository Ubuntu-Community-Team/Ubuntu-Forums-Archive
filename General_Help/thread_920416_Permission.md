---
title: "Permission?"
date: 2008-09-15
forum: General Help
---

### Post by techboy10 on 2008-09-15
Ok, Im a complete Linux noob so far and I recently install Ubuntu 8.04 on my Dell M1530 so I could use it for my computer class in college. Now I checked out the touchpad fix in the Dell help forum because my touchpad was going crazy and Im Having to use a mouse right now. I added the i8042.nomux=1 to the right part in the boot/grub/menu.lst but when I go to save it, it says I do not have the require permissions. What do I have to do to be able to save this file?


Thanks

---

### Post by howefield on 2008-09-15
> **techboy10 said:**
> Ok, Im a complete Linux noob so far and I recently install Ubuntu 8.04 on my Dell M1530 so I could use it for my computer class in college. Now I checked out the touchpad fix in the Dell help forum because my touchpad was going crazy and Im Having to use a mouse right now. I added the i8042.nomux=1 to the right part in the boot/grub/menu.lst but when I go to save it, it says I do not have the require permissions. What do I have to do to be able to save this file?


Thanks

edit the file by using sudo before the command,..   sudo gedit /boot/grub/menu.lst

---

### Post by techboy10 on 2008-09-15
Can you explain how to do that in a little more depth? Like I said, I am a complete Linux noob.

---

### Post by howefield on 2008-09-15
Sorry, open a terminal (Applications > Accessories > Terminal) and type the command into the terminal window. You will be prompted for your password, type it in and the file should open up ready for editing.

Because you have opened the file with elevated permissions by using the sudo command, you should be able to save it after you have finished editing.

---

