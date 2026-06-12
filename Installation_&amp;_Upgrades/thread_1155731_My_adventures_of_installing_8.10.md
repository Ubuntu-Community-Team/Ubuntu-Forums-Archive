---
title: "My adventures of installing 8.10"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by PCFascist on 2009-05-11
First I would recieve some I/O errors from device sr0 which I searched and found that this is the CDROM, some claim I should burn the disc at 4x, what I found was important was that I had to burn it as "disc at once", which is a current bug.

After burning it using disc at once, my problems didn't stop. I press f6 during boot to remove the quiet splash -- at the end, I then add floppy=off all_generic_ide irqpoll. Or my system would hardlock.

The install freezes for a few minutes while it fails to identify a few ata devices. (I had already changed my bios to make sure my hard drives are in "ide" mode, not AHCI). But if I wait for a while, even though it shows me a busybox prompt, I get past it and it continues to load.

It then would freeze on my 5 year old five button MS mouse, which I've used under many other linux/freebsd systems.

After replacing the mouse with a ps/2 mouse, I'm now formatting the drive in the installer!

Now, I'm really tempted after it taking two days to figure this all out to stripe my drives and try to get to the installer again.




Link to bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266951](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266951)

---

