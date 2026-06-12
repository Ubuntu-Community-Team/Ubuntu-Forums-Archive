---
title: "Ubunbtu won't boot after getting sound to work"
date: 2005-08-19
forum: Hardware &amp; Laptops
---

### Post by fmpuk on 2005-08-19
After downloading the latest alsa driver, and then compiling it with the configure command as:
./configure --with-cards=atiixp --with-sequencer=yes
sudo make
sudo make install

Then I add some stuff to module.conf i think it was. Sound does then work, but when I reboot, it doesn't show the login screen. It just gives me a terminal log in. If I go startx it does load but after rebooting it does the same.
What is going on?

---

### Post by fmpuk on 2005-08-19
[QUOTE=fmpuk]After downloading the latest alsa driver, and then compiling it with the configure command as:
./configure --with-cards=atiixp --with-sequencer=yes
sudo make
sudo make install

Then I add some stuff to module.conf i think it was. Sound does then work, but when I reboot, it doesn't show the login screen. It just gives me a terminal log in. If I go startx it does load but after rebooting it does the same.
What is going on?[/QUOTE]
 Update: If I run startx it DOES boot fine. But I seem to be missing some options in the menus and stuff (I couldn't find the login screen option at all..). How could alsa have caused all this?

---

