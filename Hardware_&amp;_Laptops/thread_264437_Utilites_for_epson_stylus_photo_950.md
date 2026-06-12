---
title: "Utilites for epson stylus photo 950"
date: 2006-09-24
forum: Hardware &amp; Laptops
---

### Post by john comfort on 2006-09-24
Epson stylus photo 950 printer installed (USB) with Ubuntu 6.06 OK and prints, but can't find the utilites which give ink levels, clean heads, print test patterns etc. What is needed to to get these to work ? Have suspicion that have seen these utilities with other distros, Kubuntu/KDE ??

---

### Post by zxee on 2006-09-25
They are available try 'sudo apt-get install escputils'
There's a gui interface too, but I don't recall the filename.

---

### Post by Trekos on 2006-09-25
mtink is the package name you are looking for.
Been there, done that. ;)

---

### Post by john comfort on 2006-09-26
Thank you (both) for directing me towards escputil and mtink. Will check them out when I have a moment.

---

### Post by john comfort on 2006-09-27
'photo 950 plugged into USB has device file /dev/usblp0 
device file owned by root so need to do         sudo mtink     in terminal
to start mtink and access printer.:-D 
(shows only one of the two black ink cartriges used by the '950)

---

