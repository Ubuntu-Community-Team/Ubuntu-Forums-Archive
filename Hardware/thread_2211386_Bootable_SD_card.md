---
title: "Bootable SD card"
date: 2014-03-15
forum: Hardware
---

### Post by kelamahim on 2014-03-15
Hi!

Im following the instructions here:

[http://linux-sunxi.org/Bootable_SD_card#Bootloader](http://linux-sunxi.org/Bootable_SD_card#Bootloader)

but I can`t find the cardroot command... Looks like it is not in the debian repositories...

Any suggestions?

Thanks,

Miha

---

### Post by dniMretsaM on 2014-03-17
Cardroot is not a command. It is a variable that you're setting.

---

### Post by kelamahim on 2014-03-17
[FONT=arial]Sorry, I somehow did not see the assigment sign..

I have another question:

Does the dd command erase the flash memory before writing to it? Would it be reasonable to erase the entire card using [/FONT]

dd if=/dev/zero of=${card}

[FONT=arial]?

I assume that when the card is new/empty, then there are just zeroes on it, however if it is partitioned with some sort of file system it has to have some data on it somewhere. Am I right?

Thanks,

Miha 
[/FONT]

---

