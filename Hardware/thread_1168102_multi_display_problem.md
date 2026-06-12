---
title: "multi display problem"
date: 2009-05-23
forum: Hardware
---

### Post by bogu. on 2009-05-23
I have a problem when I want to  switch the image displayed from my Dell laptop's lid to a external display(such as a TV). Normally, I can do this from the keyboard - with a special key, but in Ubuntu it doesn't work. What can I do ? Thank You.

---

### Post by Kareeser on 2009-05-23
If you're using an Intel graphics card, I believe you can set dual monitors (or cloning) in System -> Preferences -> Display.

I've found better success using the terminal command xrandr.

---

### Post by bogu. on 2009-05-24
But I don't have any "Display" in System > Preferences.

---

### Post by Kareeser on 2009-05-24
Er... what version of Ubuntu are you using?

Type the command "lsb_release -a" in the terminal.

---

### Post by bogu. on 2009-05-27
Distributor ID:    Ubuntu
Description:    Ubuntu 8.10
Release:    8.10
Codename:    intrepid

---

### Post by Kareeser on 2009-05-27
Is there an option in the same menu called "Screen Resolution"?

Try typing "gnome-display-properties" into the terminal.

---

