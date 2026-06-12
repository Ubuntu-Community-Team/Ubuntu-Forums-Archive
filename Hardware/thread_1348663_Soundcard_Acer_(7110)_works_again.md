---
title: "Soundcard Acer (7110) works again"
date: 2009-12-07
forum: Hardware
---

### Post by rudy.111 on 2009-12-07
Hello;

Maybe this might be a help for Acer-laptop-users with sound-problems:

My Acer 7110 Aspire does make sounds again (after install no problem, after update-session -> silence):

Solution:

-- alt-<F2>
-- execute: seek for terminal as root (gksu /usr/bin/x-terminal-emulator)
type in: 
     cd /etc
     cd /modprobe.d
     gedit alsa-base.conf
go to the last line and comment this line:
     #options snd-hda-intel power_save=10 power_save_controller=N
add as last line: 
     options snd-hda-intel model=acer 

Close all, restart, greetings, Rudy

---

