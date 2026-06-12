---
title: "can't get smartcard reader to work"
date: 2009-04-10
forum: Hardware
---

### Post by romanos.tsomos on 2009-04-10
Hi,


I recently Installed Ubuntu 8.04 
on an HP 8710w Laptop (more info on[linlap.com]("http://www.linlap.com/wiki/hp-compaq+8710w"))

Everything (including volume+wifi+calculator touchcontrols) works fine right away apart from the
- smartreader
- fingerprint reader

Now I want to make the smartcard reader work.


From linlap.com I know the smartcard reader works on linux, specifically with these drivers "kernel driver (ricoh_mmc, sdhci, mmc_block)".

When I put in a SD card, nothing happens. Nothing gets mounted automatically, nothing appears neither on Places/Computer, Gparted or Storage Device Manager.


Could someone please indicate how I can make Ubuntu use the kernel driver(s) for the smartcard?


I've been searching it up on google, ubuntuforums for more than a week now, but without any luck.

I am attaching the dmesg log in 2 parts (at least what I was able to copy out of the terminal..)


Thanks for any help
romanos

---

### Post by Padraig Notlad on 2012-10-21
This may be a little late for you, but, I just stumbled across your thread.  I have an 8710w and I'm using 12.04, and my SD card reader doesn't work either.  I found this work around though.

After you insert the card, run these 4 commands from a terminal.
My computer appears to be frozen afterwards, but after 10 seconds or so, it comes back, and I can see the contents of my SD card.

sudo modprobe -r r852
sudo modprobe -r sdhci_pci
sudo modprobe r852
sudo modprobe sdhci_pci

Hope it helps!

---

### Post by howefield on 2012-10-21
Thanks for the extra info.

Old thread back to sleep.

---

