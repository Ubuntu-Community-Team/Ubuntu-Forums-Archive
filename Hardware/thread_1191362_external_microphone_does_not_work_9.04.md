---
title: "external microphone does not work 9.04"
date: 2009-06-18
forum: Hardware
---

### Post by tytus on 2009-06-18
I have Dell Latitude D620 with Ubuntu 9.04. My internal microphone is working well but I am trying to get my external one to work. Anybody had any success in this area?

---

### Post by A. J. Rimmer on 2009-06-18
This might be as simple as unmuting the external mic or turning the gain up.  I prefer using alsamixer in a terminal to do this.  (Seems like there's a volume control somewhere in the menu system but I forget where because I never use it -- I use alsamixer instead.)

If you're not familiar with it, open a terminal and enter alsamixer.  You will see output "sliders"; use left/right and up/down cursor keys to navigate and set, usually spacebar or "M" key to mute/unmute. Press tab to show input settings, tab again to show both, tab again to show output, etc.  It's pretty intuitive.

---

### Post by tytus on 2009-06-20
Thanks. alsamixer worked. I had to press TAB once to get to input page and switch to Front Microphone.

This settings are impossible to find using the new gnome pulse audio setup :\

---

### Post by A. J. Rimmer on 2009-06-20
Yea!

Alsamixer is a great tool.  I sometimes use an external sound card with my laptop, and alsamixer gives me quick access to its settings.

alsamixer -c0 for first card

alsamixer -c1 for second card

etc.

---

