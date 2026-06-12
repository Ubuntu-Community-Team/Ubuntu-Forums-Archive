---
title: "USB hard drive removal error"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by Blake Morgan on 2007-04-05
Up front, I'm running Edgy with all the current updates.

OK, I made a dumb mistake. I unplugged a USB hard drive without first unmounting it. Now Ubuntu seems to have permanently got the thing out there, and I can't re-mount it. For instance, if I look under Places > Computer, the drive is still listed, but I can't remove it or unmount it. 

I know this has to be a simple fix, but I just can't put it together. Is it a process I have to kill? Is it something else? When I enter "lspci" into a terminal I can't put my finger on what exactly is the drive. I know that linux recognizes several different parts of the removable hard disk as separate "devices", for instance, the actual drive is one thing, the hard disk controller chip is another thing, and the actual usb connector chip is yet another thing. "ps aux" delivers equally obscure results. I think it should be simple enough to log in as root and unmount or remove the drive, but Ubuntu has too systemic protection to make that a straight-forward task. I just want to open a terminal a sudo my troubles away...

This is a generic enough problem in my mind that the actual hardware details shouldn't matter too much, but for what its worth, the removable drive in question is  an Archos Jukebox Studio 20 (an .mp3 player), but as far as linux knows, it is just a removable usb mass storage device.

---

### Post by kidders on 2007-04-07
> **Blake Morgan said:**
> I just want to open a terminal a sudo my troubles away...That is exactly what I would suggest! See if you can have Linux do a forced or lazy unmount, maybe.

---

