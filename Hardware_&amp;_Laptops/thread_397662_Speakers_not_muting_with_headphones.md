---
title: "Speakers not muting with headphones"
date: 2007-03-30
forum: Hardware &amp; Laptops
---

### Post by Neuralgia on 2007-03-30
Laptop: Dell Inspiron 6400 (Core 2 Duo)
Desktop: Dell Dimension 8400 (P4 HT), Creative Soundblaster 2 ZS
Ubuntu Edgy Eft updated, on both

For some reason, when I plug my headphones, sound still comes out of the speakers.

On my desktop, it wasn't much of  a problem, because I just turned them off, and everything ok... or I used the alsamixer, to set headphones to mute.

On my laptop, sound still comes out. alsamixer doesn't show headphone volume, and i can't turn my speakers off.

Because of this I can't use my laptop with headphones while traveling, and this sucks.

Thanks for the help

> danielcifuentes@danielcifuentes:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7149
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


---

### Post by Neuralgia on 2007-03-30
ok, fixed it.

I used this thread

[http://www.ubuntuforums.org/showthread.php?t=302543&page=2](http://www.ubuntuforums.org/showthread.php?t=302543&page=2)

adding:

options snd-hda-intel model=dell

editing:

sudo gedit /etc/modprobe.d/alsa-base

=-=-=-=-=-=-=

Now the questions is, will this work on my desktop? dell dimension 8400?
That thread talks about laptops only

---

### Post by peter771 on 2007-12-06
The fix mentioned above didn't fix my problem!
I'm running Ubuntu/windows on a Toshiba Satellite Pro A120 Laptop computer, when I plug my headphones into the jack on the front whilst running linux the speakers do not mute but when I plug the headphones in whilst running windows the speakers DO mute, therefore I beleive this is an issue with alsa and am wondering if there is a fix available?

---

### Post by spantch101 on 2008-03-05
i am having same issue with my Satellite A200 - AH1.... would appreciate a reply

---

### Post by quixotic-cynic on 2008-04-30
I've had the same issue since Feisty I think (can't remember if Dapper was a prob).

I have an A120 too. I'm trying some more things again (I gave up the last 2 major attempts) and I'll post if I find something.

---

