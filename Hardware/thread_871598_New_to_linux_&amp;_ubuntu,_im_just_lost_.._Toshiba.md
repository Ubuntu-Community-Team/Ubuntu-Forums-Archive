---
title: "New to linux &amp; ubuntu, im just lost .. Toshiba p105"
date: 2008-07-27
forum: Hardware
---

### Post by seedo on 2008-07-27
**(Solved**)Hi, im new to Linux i have been using windows based OS all my life, but l felt an urge to change i got fed up of all the crashing and i decided to try Linux.  so i installed Ubuntu on my Toshiba p105 laptop. i had some troubles with the sound and the SD card reader ( they are not working ) . so i tried to get help from this site   [http://www.linlap.com/wiki/Toshiba+Satellite+P105](http://www.linlap.com/wiki/Toshiba+Satellite+P105)   .. i discovered that there was some kind of a conflict due to "ACPI" and a "DSDT"..  actually i got lost and couldn't do a thing , i didn't even know where to put the commands  . 

even when i installed hardinfo by typing " sudo apt-get install hardinfo "

. i think i messed up, a shortcut should appear in the Applications>system tools> 

but there is nothing 
i even tried installing it from synaptic package manager


____________________________________---


SO COULD ANYONE KINDLY DIRECT THREW A DETAILED GUIDE ON SOLVING THOSE ISSUES ... 

if u would like to help threw voice chat over skype or msn ... there is no problem with me

(Solution)

i updated the BIOS to v4.30
BIOS update could be downloaded from Toshiba website 

If your not sure about your exact p105 sub series its one BIOS update for the p100-p105 models 

The sound now is working

---

### Post by geenux on 2008-07-27
If there is no entry in the menu, you can try to launch the program with Alt+F2 and enter the name "hardinfo" (without the quotes).
If its work you can add manually an entry in the menu.

---

### Post by Sef on 2008-07-27
> i think i messed up, a shortcut should appear in the Applications>system tools>

but there is nothing 

Check System > Preferences > Main Menu > (see if it is there) > if so, then click on the box next to it.

---

### Post by seedo on 2008-07-27
ya the alt+f2 worked thx ... now remains the main problem ... to get the sound working

---

### Post by hotweiss on 2008-07-27
> **seedo said:**
> ya the alt+f2 worked thx ... now remains the main problem ... to get the sound working

Try this:

sudo nano /boot/grub/menu.lst

and then add acpi=off at the end of this line:

kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda5 ro quiet splash

(basically at the end of your first grub menu entry)

---

### Post by seedo on 2008-07-28
> **seedo said:**
> 
(Solution)

i updated the BIOS to v4.30
BIOS update could be downloaded from Toshiba website 

If your not sure about your exact p105 sub series its one BIOS update for the p100-p105 models 


The sound now is working

______________________________________________________

---

