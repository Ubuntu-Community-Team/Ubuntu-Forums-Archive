---
title: "[SOLVED] Samsung YH-820"
date: 2008-06-18
forum: Hardware
---

### Post by soccerboy on 2008-06-18
I have a Samsung YH-820 MP3 player.  I tried to use the MTP plugin with rhythmbox to transfer music onto it...didn't work.  I installed easypmp to try but it doesn't recognize my player.  How can I get this working?  This is the last thing keeping windows on my computer.

---

### Post by soccerboy on 2008-06-18
bump..  also, if no one knows of a working lib with this mp3, does anyone know what is database file on this system?  That way I can poke around and see if I can write a script to update the db once I add/delete songs.

---

### Post by soccerboy on 2008-06-18
bump...anyone?

---

### Post by soccerboy on 2008-06-19
Alright, I got my mp3 working with easypmp by first calling the command,
easypmp -c -d samsung_yh820 /media/YH-820

Then everytime I add a song, I can run
easypmp -u -d samsung_yh820 /media/YH-820

Anyone know how to integrate this stuff into rhythmbox or if there is one plugin already for rhythmbox

---

