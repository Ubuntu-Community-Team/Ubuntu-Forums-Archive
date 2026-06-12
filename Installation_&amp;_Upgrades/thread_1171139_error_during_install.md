---
title: "error during install"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by drifter129 on 2009-05-27
when trying to run ubuntu from the live cd or trying to install ubuntu, i am getting the following message:

[313.188000] ata2: (irq_stat 0x00000040, connection status changed)
[315.528000] ata2: exception Emask 0x10 SAct 0x0 SErr 0x40c0000 action 0x2 frozen.

the message just repeats again and again...

i don't have anything connected to the 2nd sata port. i have also tried different distro's and getting exactly the same error.
i have also tried the boot option pci=nomsi that someone suggested, but has not resolved the problem.

can anyone tell me what the error means?
i am wandering if the error is linked to the dvd-rw drive i have connected - it is a pioneer blue-ray player.

---

### Post by glotz on 2009-05-27
The LiveCD offers you some kind of help you can access before booting it. The function keys if I remember correctly. You can try some special kernel parameters dealing with your drives.

Also, [http://bluraysucks.com/](http://bluraysucks.com/)

---

### Post by hal8000 on 2009-05-27
Not sure if this will help:
[http://ubuntuforums.org/archive/index.php/t-858926.html](http://ubuntuforums.org/archive/index.php/t-858926.html)

Also, you could try removing the cables from your Blu Ray and install Ubuntu again.  I had a similar ata message with earlier versions of Ubuntu, Feisty, I think it was.
I have an IDE and a SATA hard drive in the same computer. Had to remove the cables on the IDE HD before feisty would install.

---

### Post by drifter129 on 2009-05-27
is there anywhere i can find a list of these boot options and what each one does?

---

### Post by glotz on 2009-05-27
Here's the children's version [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Here's the entire shebang [http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

Maybe try the irqpoll switch. Failing that the no and off options under F6.

---

### Post by drifter129 on 2009-05-28
have tried the no and off options under f6, also tried adding irqpoll, all_generic_ide and pci=noacpi.
still getting the same message repeating.
have also disabled the smart function in the BIOS but still same error.

---

