---
title: "USB Keyboard"
date: 2013-08-27
forum: Hardware
---

### Post by 3dmatrix on 2013-08-27
I have an external USB keyboard attached to my laptop.
I have noticed, when i shutdown my computer and start it again, i can use the external keyboard at BIOS or GRUB stage and ofcourse later also but if i soft restart my computer i am not able to use my external keyboard till i reach the Ubuntu login stage. Is it a normal activity ? If not what is the problem ?

---

### Post by 3dmatrix on 2013-08-28
Can any one help ?

---

### Post by kurt18947 on 2013-08-28
You might be seeing what I've seen with some USB keyboards and not with others.  I'll preface this by saying I'm no expert but this is how it appears to me.  In order for a PC to recognize a USB keyboard, it has to either have that capability built into its BIOS or failing that, using an O.S. driver.  I'm guessing that a warm boot doesn't 'go back' far enough to re-initialize the USB keyboard driver code.   If relying on an O.S. driver, the O.S. must first load, at least partially.  I've seen a difference with other hardware recognition between warm boot and cold boot as well, so it's not just keyboards.

---

### Post by 3dmatrix on 2013-08-31
Thats informative. I did not know that. So if i change my keyboard, that 'might' solve the problem ?

---

