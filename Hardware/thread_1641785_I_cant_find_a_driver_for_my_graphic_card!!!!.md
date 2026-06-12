---
title: "I cant find a driver for my graphic card???!!!!"
date: 2010-12-09
forum: Hardware
---

### Post by conexo on 2010-12-09
Hi guys, look i have a VAIO VPCF115FM with a NVIDIA GeForce 310M, Intel i7 processor.
And i cant find the driver for my graphic card, and every time that i turn on my computer it show me a black screen and nothing more, Ihave read in the forum that is a driver problem.

Please if someone can help me i cant find a solution, i have install the driver or the supose driver for my card, but when i restart the computer nothing, again the black screen.

Pls Help me.

---

### Post by sikander3786 on 2010-12-09
Welcome to the forums :-)

Press and hold down Shift key from Bios screen. Grub menu should pop up. Highlighting the first entry, press 'e' to edit it. Navigate to words "quiet & splash", delete them and type "nomodeset" in their place. Press Ctrl + X to continue boot. Hopefully it should boot to the desktop successfully this time.

Now go to System > Administration > Additional Drivers/Hardware Drivers and see if any driver is activated. If not, activate the current one.

If it is already activated, please post which version driver is that.

---

### Post by karthick87 on 2010-12-09
+1 on post #2

---

