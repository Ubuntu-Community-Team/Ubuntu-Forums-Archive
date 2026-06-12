---
title: "IBM ThinkPad i series 1300"
date: 2011-11-19
forum: Hardware
---

### Post by catlover2 on 2011-11-19
Hello, I recently got an old IBM ThinkPad i series 1300, 
700 Mhz celeron 
184 MB/RAM
10Gb HDD
Trident CyberBlade A1i VGA card 
So far I have not been able to get Linux to boot on it, it hangs at "Setting up system devices..."
All I really want is a command-line only Ubuntu installation, but I'll go with LXDE if I can.

---

### Post by gordintoronto on 2011-11-19
If command-line will do, grab Ubuntu Server and install that.

---

### Post by catlover2 on 2011-11-19
I'd love to, but it hangs at a black screen immediately after pressing 'install Ubuntu server', same with all Linux livecds I've tried. 

any ideas?

---

### Post by gordintoronto on 2011-11-20
Oh, darn! This might help: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by catlover2 on 2011-11-20
I normally use the minimal CD for installing anyway, and it hangs instantly after pressing install (or command line install) from the isolinux menu.:(

---

### Post by gordintoronto on 2011-11-21
It seems likely that the old computer just doesn't have enough memory for Ubuntu. I think even the "lightweight" variants (lubuntu and xubuntu) need more than 184 MB for installation.

I haven't tried Puppy for a couple of years, but it might be OK.

---

### Post by catlover2 on 2011-11-22
Puppy sticks at 'Loading drivers needed to access disk drives'...
BTW, I do like Puppy on my other slightly more modern laptop.

---

### Post by catlover2 on 2011-11-22
I found a verbose option in the puppy boot menu:
```
ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
ohci_hcd 0000:00:14.0: guessed PCI INT A -> IRQ 10
ohci_hcd 000:00:14.0: OHCI Host Controller
ohci_hcd 000:00:14.0: new USB bus registered, assigned bus number 1
ohci_hcd 000:00.14.0: irq 10, io mem 0x81c00000
_
```It's been there for fifteen minutes or more.

---

### Post by catlover2 on 2011-11-23
SOLVED.

I added 'nousb' to the isolinux boot parameters and subsequently to GRUB, now it boots (and installs) Ubuntu Server perfectly.

I will only be using this as an Armagetron server, so I don't need USB anyway.

---

