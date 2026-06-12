---
title: "uninstalling ubuntu"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by mohd on 2009-09-26
hello there , 

i have used ubuntu for few months , but now i have to get back to windows because there are some programs i need to use in school that i can't install to ubuntu

so in short i formated my hd , but for some reason xp couldn't read my hard disk at all while windows vista and seven could , so i used them to convert my hdd to ntfs , and tried again to use xp but still the same problem
the thing is i want to use xp on that laptop cause it kinda old to keep up with the vista and 7

anyone plz ?

---

### Post by aysiu on 2009-09-27
Can you tell whomever told you to format your drive to tell others to use Wubi again in the future?

Wubi allows you to set up a dual-boot with Windows and then easily uninstall Ubuntu as you would any other Windows program (Start Menu > Control Panel > Add or Remove Programs > Ubuntu).

Do you perhaps have a SATA drive? I know XP's installer has some issues with that.

---

### Post by rannuG on 2009-09-27
You could also install Windows on VirtualBox. It's in Add/Remove.

---

### Post by MyLegIsCramped on 2009-09-27
If it's a SATA HDD then you can look in the bios and check to see the settings of your SATA controller. If it's set to AHCI then change it to IDE. Windows XP doesn't readilly come with an AHCI driver since it XP was released before SATA was standardized. You can actually use a program I believe is called nLite to add a driver to an XP ISO.

If you want to use AHCI and don't want to go through the process of adding the driver to your ISO then turn AHCI off install windows get the driver install it and then turn AHCI on again.

---

### Post by mohd on 2009-09-29
yea its a sata , and i think i tried the bios thingy but didn't work

i'll try wubi and see what happens , thanks

---

### Post by mohd on 2009-09-30
I can't find wubi in ubuntu

---

