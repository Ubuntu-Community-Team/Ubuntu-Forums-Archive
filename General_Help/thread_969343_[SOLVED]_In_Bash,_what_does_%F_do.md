---
title: "[SOLVED] In Bash, what does %F do?"
date: 2008-11-03
forum: General Help
---

### Post by Bender2k14 on 2008-11-03
In Bash, what does %F do?

Specifically, the command executed when I click on "Transmission BitTorrent client" (in Applications->Internet) is "transmission %F".  I did some searching (which is hard to do when you are looking for a something containing the percent (%) symbol) and believe that it is an argument to bash and not to transmission.  In the man pages for transmission, there is no mention of any parameter using the percent (%) symbol or the letter F (or f).

Based on [this reference]("http://www.gnu.org/software/bash/manual/bashref.html"), percent (%) can be used to name jobs, but how is naming the transmission job F help anything?

---

### Post by Slim Odds on 2008-11-03
It's not bash

bash is a console shell.

When you click on stuff that's a GUI thing.

Check the GNOME docs

[http://library.gnome.org/users/user-guide/stable/launchers-properties.html.en](http://library.gnome.org/users/user-guide/stable/launchers-properties.html.en)

---

### Post by Portmanteaufu on 2008-11-03
Basically, the %F says that the command expects there to be a list of files following the word "transmission" in the actual command. If you were to drag a few .torrent files onto the transmission launcher, it would replace the %F in the launcher command with the names of the .torrents you were dragging.

---

### Post by Bender2k14 on 2008-11-03
I see, thanks.

---

