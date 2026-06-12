---
title: "Soundblaster awe64 value (ct4520)"
date: 2013-03-08
forum: Hardware
---

### Post by Virusmike on 2013-03-08
Xubuntu 12.04
Got a pentium 3 all the hardware is well detected exept for the soundcard SOUNDBLASTER AWE64 VALUE (CT4520) i try several thing on several day and i cant have any result exept that my noise comming out that card change when i assing the ISA slot to irq5 in the bios

i try what it listed here [https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs) 

(Type "sudo nano /etc/modules" in terminal, then add "snd-sbawe" at a  separate line, save, quite, restart. For 8.10- additionally add user  (here x) to group audio by "sudo adduser x audio" and reboot.)

it wont work. at worst i will install xubuntu 8.10 but before i wondering if there any way

i tryed to modprobe snd-sb16 . then alsamixer in consol...say there not such directory (the file is in /etc/modul/ i check it)
even uninstall reinstall alsa-utils wont work.. i get the apt gnome alsa mixer in the ubuntu store... ass soon i click on hardware the apt crash

and at last i tryed what writed on [http://www.alsa-project.org/main/index.php/Matrix:Module-sbawe](http://www.alsa-project.org/main/index.php/Matrix:Module-sbawe)

i cannot get past 

 cp /downloads/alsa-* .

am am not sure i did get the right git with the command

git clone [git://git.alsa-project.org/alsa-driver.git](git://git.alsa-project.org/alsa-driver.git)

so far i try several thing and i dont have any clue to what i should try next so if you have any sugestion it would be awesome

---

### Post by kostkon on 2013-03-08
This [ubuntu wiki page]("https://help.ubuntu.com/community/HowToSetupSoundCards") has some additional instructions for ISA cards.

Generally, I would avoid ISA cards, even on a Pentium 3. You could, for example, buy a soundblaster live! (even the 5.1 version) on ebay for less than $10.

Hope that helps.

---

