---
title: "initrd extends beyond end of memory"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by intricacy on 2009-05-24
Hey guys, I burned ubuntu-9.04-desktop-amd64.iso to a thumb drive and tried to install it on a Dell Inspiron 1525 notebook. However, after I chose the option "Install Ubuntu" in the boot menu, the error message shown below was displayed and the machine halted: [I]

Here's the error message:
[/I][I][  0.000000] initrd extends beyond end of memory (0x7f66d0cd > 0x7f66d000)
 [  0.000000] disabling initrd
 [ 3.072830] Kernel panic - not syncing: VFS: Unable to mount root fs on
 unknown-block(8,1)[/I]

I've checked the MD5 of the iso file and it is fine. An annoying thing is, the thumb drive works well on another computer.

The dell computer has 2GB of memory and Intel Core2 Duo T5550.

I have been haunted with this problem for a few days. I really appreciate your help.

---

### Post by milton1 on 2009-05-24
this sounds like not enough memory, but 2GB should be way more than adequate. Have you tried running memtest? Or possibly pull you ram sticks one at a time (assuming 2 or more in your system) to see if one is bad. Even 1GB RAM should be plenty to run the install.

---

### Post by milton1 on 2009-05-24
OK, checking the HEX value for the memory in the error above yields 2,137,444,557 which is more than 2GB. For some reason, your initrd is trying to load into a HUGE amount of memory. I'm sorry, but I have no idea why.

---

### Post by intricacy on 2009-05-24
> **milton1 said:**
> OK, checking the HEX value for the memory in the error above yields 2,137,444,557 which is more than 2GB. For some reason, your initrd is trying to load into a HUGE amount of memory. I'm sorry, but I have no idea why.

Thanks for your help!

I did a calculation and found it actually less then 2GB (*0x7f6.6d000 is about 2038M Addresses*.)

I found a relevant bug report [here]("https://bugzilla.redhat.com/show_bug.cgi?id=493409") where someone posted a solution. But I don't know how to add the "kernel options".

---

