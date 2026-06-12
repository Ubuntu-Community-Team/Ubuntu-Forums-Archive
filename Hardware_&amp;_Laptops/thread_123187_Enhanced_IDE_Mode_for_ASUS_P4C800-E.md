---
title: "Enhanced IDE Mode for ASUS P4C800-E?"
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by gunnor on 2006-01-29
Hi folks,

I have a minor problem when either trying to use the LiveCD 5.10 or when trying to install ubuntu 5.10:
In the BIOS of my mainboard ASUS P4C800-E Deluxe, I have an option to switch the IDE mode either to Native or Compatible.
If the mode is set to Enhanced, I am not able to start either the LiveCD nor to install ubuntu. The setup always stops when detecting the IDE settings.
If the mode is set to Compatible, the IDE settings are successfully detected.
Because my PC hosts 2 OS (Windows XP and ubuntu) I do not want to leave the IDE mode set to Compatible as this degrades the performance of Windows XP.
Now my questions is if anyone knows if ubuntu Linux can be made compatible with the Enhanced IDE Mode of the IDE controller. Perhaps I need a new kernel? Anyone had this problem before?

---

### Post by terribleCabbage on 2006-02-18
I'm having the same problem here, except with a ASUS P4P800.

I have the following setup:
- 2 x IDE HDs
- 2 x IDE CD/DVD drives
- 2 x SATA

I can't set the mode to Compatible either, because otherwise I lose the use of two drives.

The installation failed at the same spot (trying to detect IDE settings) - the only solution I've found thus far is to switch back to Compatible mode and install. Booting works fine, etc.
As soon as I switch back to Native/Enhanced, GRUB fails with error code 22.

Any help appreciated. :)

Thanks,
Rob

---

### Post by jimmer on 2006-02-19
I have an Asus P4P800D MB. I am able to load the Live Breezy distro without difficulty. I too have 4 Hard drives and 2 DVD's Player/burners. My primary PATA controller holds 2 IDE drives. One master and the other slave. My Secondary IDE controller holds my DVD burner and player. My Sata drives are configured as Raid 0. My Bios settings are set to Enhanced mode. I never tried to install Breezy on this box. Hopes this helps.

---

### Post by mennolodder on 2007-05-05
After a long search I've finally found a solution to this, since I've done a long search myself and didn't find any answers, I'll reply to this message, eventhough its a bit old. 
I've got the P4C800 deluxe version, I haven't tried to use RAID. The ubuntu I used was 7.03.

The Short Version:

Turn on Enhanced IDE Mode and select Support On P-ATA + S-ATA in the IDE Configuration of your BIOS

The Long Version:

The trick is in getting the right IDE configuration (listed on the main section of your BIOS), note that where I use IDE, the settings use P-ATA.

You have the following options:
Onboard IDE Operate Mode [Compatible | Enhanced]
Enhanced Mode Support On (only shows in Enhanced mode) [P-ATA | S-ATA | P-ATA + S-ATA ] 
IDE Port Settings (only shows in Compatible mode)  [Primary P-ATA + S-ATA | Secondary P-ATA + S-ATA | P-ATA ports Only]

In short what the motherboard does in compatible mode is 'emulate' the SATA on the IDE controller. In enhanced mode all 4 IDE slots (non raid) and 2 sata (non raid) are available, but on the default settings ubuntus live cd will crash when detecting the IDE drives. 
In compatible mode, all works fine, but you can only use 4 drives, I have used this to install ubuntu, although I now think, that if I used the correct settings right away. The IDE POort Settings option allows you to indicate which controllers to use.

In Enhanced Mode the default setting for the 'Support On' is S-ATA and the manual doesn't explain what it really does, it just sais, that if you change it and it messes things up, put it back to S-ATA. Ubuntu wont boot with the S-ATA option, but when I just tried to change it to P-ATA + S-ATA everything worked for both Windows XP and Ubuntu and all drives were detected correctly.

---

