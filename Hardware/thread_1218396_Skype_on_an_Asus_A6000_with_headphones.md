---
title: "Skype on an Asus A6000 with headphones"
date: 2009-07-20
forum: Hardware
---

### Post by rkouere on 2009-07-20
Hi all

This is the first time I am posting a new thread so I do apologise in advance if I do not follow the right way of doing it.

My first problem was to get the headphones working on the Asus. I solved this problem when finding this thread: [http://ubuntuforums.org/showthread.php?t=201657](http://ubuntuforums.org/showthread.php?t=201657) and added the line "options snd-hda-intel model=z71v position_fix=1" in /etc/modprobe.d/alsa-base. Just for info, the A6000 uses the Realtek ALC880 sound card.
To do so: 
- open up a terminal window and type: sudo cp /etc/modprobe.d/alsa-base.conf /etc/modprobe.d/alsa-base.conf_BACKUP (this saves a backup of your current settings, just in case)
- sudo gedit /etc/modprobe.d/alsa-base.conf
- add "options snd-hda-intel model=z71v position_fix=1" at the end of the text file
- save
- restart Ubuntu

The sound should now be working with the headphones. If not, click once on the speaker icon (top right of the screen by default) and click on "Volume Control". Double check that the "Headphones" are not muted (if you can't see the settings, click on "Preferences" and tick "Headphones).

Finally, open up the options in Skype (Ctrl+O) and click on the "Sound Devices" tab. Under "Sound In", choose "HDA Intel (hw:Intel, 2)"; under "Sound Out" and "Ringing", choose "pulse", unclick "allow Skype to automatically adjust my mixer levels".

Make a test call, it should work.

Nico

---

