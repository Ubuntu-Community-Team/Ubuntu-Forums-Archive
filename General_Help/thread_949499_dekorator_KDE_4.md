---
title: "dekorator KDE 4"
date: 2008-10-16
forum: General Help
---

### Post by funky_D on 2008-10-16
hello everybody!

i want to install dekorator for KDE 4. I found a tutorial:
(hxxp://www.kde-look.org/content/show.php/deKorator?content=87921)
[I]export PATH=$PATH:/usr/lib/kde4/bin/
cmake dekorator-0.4 -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
make
sudo make install[/I]

but i get this output:
*CMake Error: The source directory "/home/dino/Programs/dekorator4" does not appear to contain CMakeLists.txt.*

i created a directory named dekorator4... but i don't have a clue what to do.. if someone has a tutorial or as gone through this situation before with success please don't hesitate sharing.

thanks all!

---

### Post by HeadHunter00 on 2010-01-01
you have to make another directory in that directory for cmake to work

---

