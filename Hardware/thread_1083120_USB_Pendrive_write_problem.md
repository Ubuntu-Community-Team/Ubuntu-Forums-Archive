---
title: "USB Pendrive write problem"
date: 2009-02-28
forum: Hardware
---

### Post by DaneV on 2009-02-28
Hi,
I have been running Xubuntu for a couple of days now and everything works fine except one thing;

When i use a usb-pendrive, reading of the files goes fine. But when i copy a file trough the Xubuntu GUI to the flashdrive it appears in the folder but it isn`t acutually written on the usb drive. When i remove it and plug it back in again, the file is gone.

When i copy it through terminal (cp file.zip /mnt/drive) a file of 0 bytes is created but that`s it.

I`ve tried three different USB-Pendrives which all are FAT formatted and work fine with my windows and mac machine.

Anyone that can point me in the right direction? I have some basic experience in linux but i have no clue on how to solve this problem. Googling it hasn`t helped me much either so far...

Thanks :)

Edit: i`m using a machine with an A8V-VM mainboard

---

### Post by taurus on 2009-02-28
Did you remember to unmount it first before you unplugged the thumbdrive?

---

### Post by DaneV on 2009-03-01
hmm, that actually worked. Can`t believe i haven`t thought of that earlier :)

Thanks

---

