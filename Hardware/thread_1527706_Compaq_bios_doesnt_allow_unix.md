---
title: "Compaq bios doesnt allow unix"
date: 2010-07-09
forum: Hardware
---

### Post by Kangarooo on 2010-07-09
when i put hardrive witch has ubuntu then bios tells:
> 
Initializing Intel(R) Boot Agent Version 4.0.19
FXE 2.1 Build 003 (WfM 2.0), RPL V2.73


The following configuration options were automatically updated:
  Disk: 10.2 GB      QUANTUM FIREBALL CX10.2A
  CD-ROM:            TSSTcorpCD-R/RW DRIVE TS-H292A
       If you are running Unix, you need to configure your system
       using the Computer Setup Utility (F10).

                                                                     Compaq


[F1: Save Changes]                         <F10-Setup> <F12-Network Sevice Boot>



i clicked F10 then exit and save and after Bios loading then Ubuntu doesnt starts..
What setting i need to change there?

---

### Post by AltomineUK on 2010-07-09
hmmm..... are u using an external hard drive or USB pen-drive?

Your ISO image must be burned in to either one. As for the BIOS, just make sure that the USB drive is at the top of the list in the "Boot Order" section.

And a final note..... Ubuntu is not Unix, but it's like Unix :D

---

### Post by Kangarooo on 2010-07-09
im using harddrive. HDD
external that isnt. so then opposite should it be called internal?
with 2 wires connected to comp to motherboard.
i dont have no ISO its already installed.
about unix thats what im beeing asked to change something in bios if its unix and since ubuntu doesnt boot up then something for unix needs to be changed.
maybe with unix they mean also linux couse they didnt write change also if linux and something more.. :)

---

### Post by AltomineUK on 2010-07-10
Hmmm... this is interesting....

Exactly what type of PC are you running Linux on? Is it old or new?..... 

Normally, if you managed to install Linux onto your HDD then, assuming the bootloader is still present, the computer should start booting Linux after moving from BIOS. According to your BIOS warning it's like the boot loader wasn't detected...

---

### Post by efflandt on 2010-07-10
Maybe you should have just hit F1.  If the drive uses a standard MS-DOS partition table you do not need to set the BIOS to unix, even if you have other Linux specific file systems.

I wonder if your drives are properly jumpered which depends on the drive controller and cable type.  If the cable is marked for which drive is which, they would usually be jumpered as cable select (CSEL).  If this is on a cable with another drive and the plugs are not marked, the drives may need to be jumpered as master and slave.

Then depending upon your BIOS, you may need to set something to boot from that specific drive, and/or press a key during BIOS splash screen to choose the boot drive.

---

### Post by luigi_mb on 2010-07-10
> **Kangarooo said:**
> when i put hardrive witch has ubuntu then bios tells:


i clicked F10 then exit and save and after Bios loading then Ubuntu doesnt starts..
What setting i need to change there?

Did you simply hit F10 and then Exit? Try again, and after hitting F10 look at the screen and check/uncheck the appropriate items. Then, and only then click on Exit.

/luigi

---

