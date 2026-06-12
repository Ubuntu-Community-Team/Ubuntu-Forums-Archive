---
title: "Won't boot after mobo swap?"
date: 2005-12-16
forum: Hardware &amp; Laptops
---

### Post by TheEHMan on 2005-12-16
Changed out my K6-III for an Athlon 900 board and processor to improve my Ubuntu experience.  Now the system won't boot up to GUI login.  It starts normally but goes to a screen saying that it couldn't start the X Server.  I can view the outputs but it doesn't give me any options to change anything.  After that it goes to a command line.  Is there some way I can reconfigure the X Server from here to get my system to start or am I doomed to reinstall?

---

### Post by Lambert on 2005-12-16
try this command

sudo dpkg-reconfigure xserver-xorg

you can read 

man dpkg-reconfigure for options.

---

### Post by TheEHMan on 2005-12-16
You guys rock!!  This is sooooooo much faster!

---

