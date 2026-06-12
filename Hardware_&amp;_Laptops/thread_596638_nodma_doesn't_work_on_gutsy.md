---
title: "nodma doesn't work on gutsy"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by racoq on 2007-10-29
Ok. Basically i have an old HD Seagate 20GB, and when i had feisty installed, i had to had the ide=nodma switch to the grub kernel entry (at /boot/grub/menu.lst), in order to Ubuntu start without messages.

I recently upgrade my computer to Gutsy and i have noticed that the ide=nodma switch at /boot/grub/menu.lst doesnt work anymore, my guess is that the kernel was not built with this option.

If i don't include this parameter in grub, i get many errors, and ubuntu takes forever to load, and display the messages below.

Is there anyway i can tell teh kernel not to enable DMA by default?

Note i tried editing /etc/hdparam.con adding dma=off  like this:

/dev/hda {
dma=off
}

And that didn't did anything, i still get those messages like

dma status == 0x21
hda: DMA timeout error
hda: timeout error: status0x58 { Driveready SeekComplete DataRequest}


Please help :(

---

### Post by racoq on 2007-10-30
Bump. Need help here

---

