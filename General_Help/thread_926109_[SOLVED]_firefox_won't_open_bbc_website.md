---
title: "[SOLVED] firefox won't open bbc website"
date: 2008-09-21
forum: General Help
---

### Post by mick222 on 2008-09-21
I just installed flash 10 using this method  [http://www.ubuntu-unleashed.com/2008/05/howto-install-flash-player-10-astro.html](http://www.ubuntu-unleashed.com/2008/05/howto-install-flash-player-10-astro.html)
I can play flash content with you tube etc but when i try to open the bbc website Firefox closes. I think it could be to do with the fact that the flash plugin is in my home directory instead of usr\lib\mozilla\plugins where it was with flash 9 how ccan i move it or should i reinstall.

---

### Post by nowshining on 2008-09-21
move it to /home/username/.mozilla/plugins and try again..

---

### Post by mick222 on 2008-09-21
I'm a newbie how do i move it i am useless with terminal and can't gain permissions

---

### Post by nowshining on 2008-09-21
is the flash lib here: /home/ur_username/.mozilla/plugins

open nautilus, press ctrl+L, then at top in the now editable location box, enter /home/ur_username/.mozilla/plugins, 

if u don't have it there, move the flash lib there by gui ie: opening up a new nautilus window, etc.. or open up the terminal

mv libflashplayer.so /home/ur_username/.mozilla/plugins

or change after mv to the folder that you have the libflash in, where exactly is that lib file located at this moment..

it should be here- example mine:/home/nowshining/.mozilla/plugins/libflashplayer.so

---

### Post by mick222 on 2008-09-21
got it i like to do thing with the gui if possible gksudo nautilis down it
seems ok now. 
The file was in home\mick\.mozila\plugins moved it to usr\lib\mozilla\plugins

---

### Post by nowshining on 2008-09-22
ah! okay i'm glad it's working for u then.. :)

---

