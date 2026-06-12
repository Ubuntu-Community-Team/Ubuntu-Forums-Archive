---
title: "can't install on asus m2a-vm with onboard ati x1250"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by supersonicdarky on 2008-01-02
I bought a computer with the Asus M2A-vm motherboard with onboard ATI x1250. The installation stalls at "running local boot scripts...". I have looked around but none of the solutions I tried work. I also tried installing ubuntu from alternate cd, fedora and opensuse. Suse successfully installed but the resolutions was too small, graphics were all in framebuffer, mouse didn't work and neither did my pci wireless card.

Some info:
- monitor connected by dvi
- default res is 1680x1050
- trying to install amd64 version
- bios version 0302 - 03/07/2007 (according to cpu-z)

Things I tried:
- disabling HPET in bios
- boot options: **pci=nomsi irqpoll noapic acpi=off**
- 32 bit cd
- safe graphics mode

Any suggestions would be appreciated as I really hate using windows. Feel free to ask for more detail.

---

### Post by intel on 2008-01-02
on grub boot menu, press "e" to get to edit screen,
& remove any options after "ro" (there may be options like "splash" & "quiet" to be removed)

press "enter"
press "b" to boot.

if you R still stuck, try the "alternate" install CD.
If at any point the system seems to be stuck,
try pressing ctrl+alt+F1 , to see any messages,
(you can try F1 to F6)

regarding problems with X1250, you may post your specific query here
[https://groups.google.com/group/x1250](https://groups.google.com/group/x1250)

---

### Post by paterick on 2008-01-21
I imght be totally wrong but i just had a smilar issue today, when i fiddeld with iommu= kernel boot parameters....

.... read the docs once, maybe, at

[http://lxr.linux.no/linux/Documentation/x86_64/boot-options.txt#L191](http://lxr.linux.no/linux/Documentation/x86_64/boot-options.txt#L191)

oh - btw. ....that's just in case u got 4gis of ram or more!

---

### Post by Yellow Pasque on 2008-01-21
When you get hung up, press Ctrl+Alt+F1
In the terminal (sudo may not be needed before the commands, not sure if LiveCD gives you auto-root privs):
```

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f --overlay-type=Xv

```
Restart X with Ctrl+Alt+Backspace

---

### Post by Yellow Pasque on 2008-01-21
The above procedure installs the Ubuntu version of Catalyst/fglrx.
If you want to try for Desktop Effects or the other features of the ATI version of the Catalyst driver, I'd suggest joining the X1250 group on google.
[http://groups.google.com/group/x1250?hl=en](http://groups.google.com/group/x1250?hl=en)

---

### Post by DuncanG on 2008-01-25
I had this problem with Gigabyte GA-MA69GM-S2H, ATI X1250. Dowloaded latest drivers from ATI (8.1, Jan 200, followed instructions and rebooted. Got a blank screen, but pressing CTRL-ALT-F7/8 ? Got the screen via HDMI. At last !

---

### Post by vmweenie on 2008-03-11
Did you ever get an install to work?  How?  

I'm running (well, TRYING to) same board with a AMD 64 X2 4400+.  I haven't been able to get an OS on it yet.    Got Fedora 8 LiveCD to finish the install (after several attempts) and, on first login when booting from the HD, I got the pixel spray (a la The Matrix, random columns of green pixels) and system hang.  Hafta power cycle. 

Run Ubuntu install in safe grafix mode, it dies at various points.  That is, the install runs to *some* point then dies, that *some* point being while copying system files, doing the partitioning, ... just some seemiongly random spot. 

Most recent BIOS (1603).   Stripped out WiFi card, bare bones as described above.  Ummm, what else... CD integrity check: OK,   memtest: OK,  

But aida on the RescueCD gives up the ghost after CPU tests.  Says "...DETECTING..." forever.  Oh, tried 32 and 64 bit.  

S'gotta be the grafix dirver, right?

---

### Post by supersonicdarky on 2008-03-13
It worked perfectly after updating the bios (1603). Not sure what your issue is.

---

### Post by seapahn on 2008-03-21
One thing that fixed my ubuntu installation freeze on this board was setting "plug and play os" to "yes" in the bios (v 1604 ).

---

