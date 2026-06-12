---
title: "Sansa Fuze and RhythmBox"
date: 2008-08-14
forum: General Help
---

### Post by SlalomMan on 2008-08-14
I just bought a Sansa Fuze, and I can get it to work by putting it in MSC mode and running "sudo rmmod ehci_hcd" and then "sudo modproce ehci_hcd". Is there anyway I can skip this? If it's completely necessary, that's fine, but now to get to the main point.

RhythmBox detects the Fuze as a USB drive, and I can drag and drop files from my library to the player. The problem is that RhythmBox just drops them in the root of the player, whereas the music needs to be in the "MUSIC" folder in the root. Is there any way to make RhythmBox think that the "portable device" or whatever is "/media/SANSA FUZE/MUSIC" instead of "/media/SANSA FUZE"? I was going to try to do something like mount /MUSIC separately, but the partition table on the Fuze is kind of weird. Any suggestions?

---

### Post by tobixyz on 2008-08-14
just put a file named .is_audio_player in the root directory of the player. into this file you write: audio_folders=MUSIC/
then rhythmbox should write the music in the MUSIC folder.
does somebody know how to force rhythmbox to put podcasts in the PODCASTS folder?

---

### Post by SlalomMan on 2008-08-14
Thanks, that worked perfectly! Do you want me to leave this topic open so your question might get answered?

---

### Post by jaygo on 2008-09-04
try running "lsusb" instead of the commands you're using. It seems to work better and doesn't require root.

---

### Post by franc00018 on 2011-05-28
> **tobixyz said:**
> just put a file named .is_audio_player in the root directory of the player. into this file you write: audio_folders=MUSIC/
then rhythmbox should write the music in the MUSIC folder.
does somebody know how to force rhythmbox to put podcasts in the PODCASTS folder?

 thanks,  this helped me with sansa fuze+ on rhythmbox 0.12.8 on debian squeeze

---

