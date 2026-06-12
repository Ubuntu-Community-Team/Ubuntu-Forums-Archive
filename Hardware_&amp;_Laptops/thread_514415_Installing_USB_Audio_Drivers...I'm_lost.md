---
title: "Installing USB Audio Drivers...I'm lost"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by dbsoundman on 2007-07-31
I'm trying to install the generic ALSA drivers for my Lexicon Omega USB audio interface but I can't seem to get things rolling. I went to [this site]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Lexicon&card=Omega.&chip=&module=usb-audio") and it described the process. I went to my terminal and started entering commands, but it said that I was denied access to create the alsa driver folder for the installation. I couldn't just change the name either. Any tips on how to get this thing to work?

Thanks,
Dan

---

### Post by fredj on 2007-08-01
Ubuntu Feisty already has drivers for compatible USB sound devices. Plug in your device, open the
Alsa mixer (double click on the speaker icon in the taskbar) then go to the File->Change Device
menu and see if your device is recognised. If not search for updated firmware for it.

---

