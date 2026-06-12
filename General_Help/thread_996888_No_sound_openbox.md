---
title: "No sound openbox"
date: 2008-11-29
forum: General Help
---

### Post by fedex1993 on 2008-11-29
Okay so this morning i have been sitting here working on getting sound working on openbox. It seems that when i load alsamixer it loads the pulsa audio instead of loading alsa mixer. Is there a bug or a way tha ti can fix this???/

---

### Post by fedex1993 on 2008-11-29
Is there a way to set the default sound device or w/e from a terminal?

---

### Post by fedex1993 on 2008-11-29
Sound is working in gnome but not openbox. I think it is when i boot into openbox it uses pulse audio by default in alsamixer. Is there a way to switch from pulseaudio to alsa from a terminal?

---

### Post by octobuntu on 2009-06-04
This probably sounds stuid, but have you tried hitting the '**M**' key under '**the master**' after typing '**alsamixer**' in the terminal?

---

### Post by sookun on 2010-03-04
thks got the same problem! solved by typing M!!!  ;-)

---

### Post by quixotic-cynic on 2010-12-01
I got the same problem recently and it was not solved by pressing M.

It occurred after I removed gdm.

Solved by adding ```
(sleep 2 /usr/bin/pulseaudio --start --log-target=syslog) &
``` to autostart.sh (running Ubuntu 10.04)

---

