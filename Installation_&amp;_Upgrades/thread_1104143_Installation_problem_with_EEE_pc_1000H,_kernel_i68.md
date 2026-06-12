---
title: "Installation problem with EEE pc 1000H, kernel i686?"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by qualtch on 2009-03-23
Hello all,

I've ben trying to install Ubuntu on my eee pc with Wubi, and also by creating a bootable USB-stick with version 8.10.

Wubi installation didn't boot to OS after reboot and I had to return to windows. There was some kind of an error message but  it disappeared always in a blink of an eye so I don't know why it didn't boot to OS.

So, after various reattempts, I decided to try an USB-stick installation. Everything went well until I tried to boot from the USB stick: It shows an error, which says something about wrong version of the kernel. It says, that it is impossible to boot from the USB device because the stick contains x86-64 kernel, while this laptop requires i686 kernel. How can I solve this? The image I downloaded is the 32bit -version...

---

### Post by qualtch on 2009-03-23
Okay then, problem solved for now... Ubuntu is installing.

I had to edit the kernel bootup line in the bootloader and it worked.
If anyone else encounters this problem, follow these instructions:

1. When in the bootloader, select "Ubuntu"
2. When the loader asks you to press Esc within 5 seconds, do it.
3. You now may choose between different Ubuntu boot options. Navigate to the first one and press "e" (for edit)
4. Select the second line (kernel) and press "e" again.
5. Add "irqpoll" to the end of the line you see.
6. Press "enter" and then "b" to boot.
7. Vóila.

---

