---
title: "Do I really need to reinstall ALL these drivers?"
date: 2012-06-02
forum: Hardware
---

### Post by ImWidUonDat on 2012-06-02
Old Toughbook CF-51 Gets new life with Ubuntu 12.04

two days ago tried Linux and fell in love.  My Toughbook has just gotten tough again.   WIn XP was making it look like a wimp! 


So, now I want to get rid of WinXP completely and plan to do a fresh install of Ubuntu - but will first do a complete wipe of the  harddrive with systemrescueCD to turn everything to zeroes.

So, I guess I need to copy drivers but I wonder which ones or all.  

Utility says I have lots of hardware on this laptop:  things like bridge, controllers, ethernet controller, Firewire etc, 4 USB controllers...  - and 12 drivers.

QUESTION:  Do I really need to download to CD all 12 of these drivers:


[LIST=1]
[*]iwL3945  (Linux/Intel wireless chip set)
[*]agpgart-intel
[*]i915
[*]snd_hda-intel (soundcard)
[*]pcieport
[*]uhci_hcd (usb drives)
[*]ata_piix
[*]i2c-i801
[*]sky2 (ethernet controller)
[*]yenta-cardbus
[*]firewire_ohci
[*]sdhci-pci (host controller bridge)
[/LIST]
Do I download them from internet or  copy from my laptop?

Thank you in advance for helping newbies like me.   Coleen
:neutral:

Thank you.

---

### Post by nothingspecial on 2012-06-02
They come included in Ubuntu, so there is no need.

---

### Post by Bucky Ball on 2012-06-02
Welcome.

You are thinking 'Windows'. No, you don't need to save them. Just install Ubuntu and you will be installing them again anyhow. 

It is really not necessary to wipe the drive with zeros if you are not disposing of it. Just boot from the install CD, 'Try Ubuntu', open Gparted (partition manager) and kill all the partitions on the drive, then install Ubuntu by clicking the icon on the desktop. 

BUT ... If you have 12.04 installed, why don't you just kill the Windows partitions and expand the Ubuntu install into the free space??? You would do this using Gparted from the LiveCD, as explained.

---

### Post by kohoutek1 on 2012-06-02
Five years ago, you would have had to install half of them, and by command line (as in compile). But now, most linuxes are plug n play. You'll still find some holes though, notably in printer drivers, but in those cases you can locate them through a google search.

---

