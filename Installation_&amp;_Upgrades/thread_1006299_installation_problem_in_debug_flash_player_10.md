---
title: "installation problem in debug flash player 10"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by bharath225 on 2008-12-09
Hi,

I have installed flash player 10 (debug version as plugin for firefox).After I've installed I restarted my system and I checked it by writing one small program in flex.Debugger is true.But when i shutdown my system the flash player which I've installed is not activated.Old version (the one i have earlier) is activated.When I shutdown my system installed version was lost.How to solve this?

And i tried to install standalone debug player but it's asking for url i don know which url it's asking?
I am getting frustration with this problem?
Anybody please help me on this....my communication will not be best please don mind for that.

Thanks
Bharath

---

### Post by igurbev on 2009-06-17
Replace ~/.mozilla/plugins/libflashplayer.so with 

... flash_player_10_linux_dev/plugin/debugger/install_flash_player_10_linux/libflashplayer.so

---

### Post by jmiguel77 on 2009-07-07
hi

i'va already done that, both using the flash installer provided by adobe and by hand

in the first case i, log off / log on and the first time it works ok, but if i close firefox and start again, it no longer works

any ideas ???

---

### Post by ducksun43 on 2009-07-07
that [http://sunoano.name/ws/public_xhtml/debian_notes_cheat_sheets.html#flash_on_debian](http://sunoano.name/ws/public_xhtml/debian_notes_cheat_sheets.html#flash_on_debian) might help you I guess

---

