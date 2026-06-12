---
title: "Installing Ubuntu from USB-cdrom"
date: 2004-12-04
forum: Hardware &amp; Laptops
---

### Post by crodler on 2004-12-04
Hi all,
I want to install Ubuntu on a Clevo T200V Laptop (Usb-keyboard IDE- HD, USB-Cdromdrive and Via Antaur processor ).

Booting is ok, loading kernel ,  etc, until ubuntu is searching for cdrom.
I found no way to mount the usb cdrom device . I think it should be mounted at /dev/scd0, or something like this. usb-storage is loaded, but in the /dev directory is no node scdx nor sdax. 

Any idea how to solve this?

I had the same problem with other debian-based distributions. 
Mandrake 9 instalation works, but crashes after booting installed system.



12/12/2004:
](*,)  Problem resoved. ](*,)   Just browsing the help screens at start.  
Instalation worked fine with this parameters:
expert vga=771 pci=noacpi bootkbd=es   (I'm from Spain)
also works just with   linux vga=771 pci=noacpi bootkbd=es

---

### Post by strips on 2004-12-04
I'm not sure about your problem.

Check dmesg output. It's always a good thing.

---

### Post by henka on 2004-12-04
:|  ... I am having the same problem with a Dell D400 ... is there a possibility to get around this problem ?

thanks for any suggestions !

---

