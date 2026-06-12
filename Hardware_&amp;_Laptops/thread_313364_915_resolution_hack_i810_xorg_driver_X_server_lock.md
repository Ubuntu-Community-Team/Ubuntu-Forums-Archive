---
title: "915 resolution hack i810 xorg driver X server lock up?"
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by n0dl on 2006-12-05
Hello, I run ubuntu on my Dell inspiron 6400 notebook. I use the i810 driver with my 945GMA integrated video card and 915resolution to correctly display the native 1280x800 resolution. While everything works pretty good I occasionally experience soft X lockups which means that things are running actively in the background (xmms, conky (my system monitor), pages loading on firefox, etc) but I cannot activate my left click menu (on openbox), nor do any of my keybinds work (ctrl+alt+backspace, ctrl+alt+delete). This happened to be on both dapper and edgy, however in Edgy (which is the release I am currently using) I have been able to successfully kill X using ctrl+alt+backspace. I tried looking in Xorg.0.log and xsession-errors (as well as /var/log/messages and ~/.xsession-errors) but to no avail. This never really happened to me (or recall ever happening) before I ran the 915resolution hack. I am just wondering if anyone is expereincing anything similar. Perhaps its the 915resolution program or the i810 driver, im not really sure. Any information would be helpful.

uname -a output:Linux l4in 2.6.17-10-server #2 SMP Fri Oct 13 18:47:26 UTC 2006 i686 GNU/Linux

---

### Post by n0dl on 2006-12-06
Ok I reproduced the problem this morning and I was able to ssh into my laptop. I tried to ps -ax | grep defunct and looked at my top output to find any defunct processes to no avail. However, when i sent a kill signal to the firefox process that was running X server died as well. Does anyone know if the ubuntu firefox packages causes X lockups?

---

### Post by sgbeamer on 2006-12-19
Yes this is happening to me all the time also.  I have an HP Pavilion slimline with the 89915G/GV/910GL Express chipset.  I get the soft X lockups after the computer has been running for a while with the screensaver on.  It's been happening for the last 2 versions of Ubuntu.  I kill the x-server to get out of it (Ctrl-Alt-Backspace) and then gdm takes over and I log back in.

---

