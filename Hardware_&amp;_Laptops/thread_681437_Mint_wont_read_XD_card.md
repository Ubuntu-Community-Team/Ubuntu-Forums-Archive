---
title: "Mint wont read XD card"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by vociferous666 on 2008-01-29
Specs:
Linux Mint 4.0 Daryna
Compaq Presario v2630us
Texas Instruments Card Reader
AMD Turion
512 MB RAM
ATI graphics

everything on the system except the card reader works fine

ok so when i insert an XD picture card the status light blinks once and then does nothing,
the computer recently had XP on it and XP read the XD card

linux will not mount automatically mount the volume.
i cant find how to manually mount the volume.
when i did  LSPCI in terminal i get a Texas Instruments SD blah blah blah.  
its my girlfriends computer and i dont have access to it today or else i would post more info.
when i inserted an SD card into the slot, the status light lit up and blinked and the card popped up on the desktop.

i am running the same linux on my laptop
Ricoh card reader
nVidia graphics

AMD Turion X2
dual boot XP MCE
mine will not read the card either, but when i boot to XP it asks if i want to format the card

i inserted the card into a newer compaq laptop running xp pro and it read the card just fine

how can i see if linux even sees the card?

how can i manually mount the card and activate the volume? its fat32

if none of this works, is it possible to reinstall/recompile the drivers?

is the driver in more than one part, could the XD driver be screwed if SD works fine on the same reader?

im very curious about all of these things.

---

### Post by vociferous666 on 2008-01-30
ok heres the info from LSPCI

05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

so there is the printout minus her other hardware i also have that one if anyone wants to see it

ANYONE!!!!!

it has SD and MMC support along with a firewire port and of course a USB port.  now it also has support for XD but im not seeing that as a device.  since its not one piece of hardware but a couple pieces of hardware bundled, me thinks its missing a driver.

---

### Post by kegobeer on 2008-01-30
Well, since I don't run Mint, all I can recommend is to install Ubuntu and see if that works.  If you want to use Mint, you might get better help from Mint users on the Mint website.  (Mint is built upon Ubuntu, so it isn't really Ubuntu.)

---

### Post by vociferous666 on 2008-02-02
ubuntu works exactly like mint does.

i started the ubuntu live cd and it does the same exact thing.

and since mint works just like ubuntu and has the same exact problem what do you think the solution is?

---

### Post by ispy on 2008-02-23
i'm bumpiing because i have the same problem and it's killing me. i can't access the pictures on my camera!

---

