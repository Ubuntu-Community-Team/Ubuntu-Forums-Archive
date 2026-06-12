---
title: "Firefox running issues"
date: 2008-08-08
forum: General Help
---

### Post by thestig_992 on 2008-08-08
A while back my firefox suddenly stopped working properly, meaning that the pages only seemed to display basic text, with no formatting or pictures.

After deciding i couldnt work out how to fix it, i reinstalled firefox following a guide, which involved removing some directories (possibly and /usr and /etc) then using sudo apt-get remove firefox, or along thse lines

Then i followed the instructions on how to reinstall, this was basically doing the reverse. Since then i have not been able to run firefox properly at all. For starters I cant run firefox by typing firefox into a terminal. I have to run it by running the executable in my download directory. 
Secondly, my flash player will not install. When i try either the recomended way (involving choose your player then clicking install, from a popup box), it didnt have most of the usual players, such as gnash and icedtea...only adobe flas player. When i tried this it said could not install.
I then tried installing it manually, but adobe did not seem to recognise that firefox was installed (i assume that this has something to do with the inability to run firefox properly from a terminal...

---

### Post by Thyssenkrupp on 2008-08-08
run:

sudo dpkg --configure -a

i had problems with my flash and that helped.

i dont know exactly what it does, i tihnk it installs what needs to be installed to fix any problems.

e.g. flash has started the instlalation process but stopped halfway through, tht command will fix it.

and if it doesnt then its not gunna do anything bad to your computer.

hope i helped.

Jak

---

### Post by thestig_992 on 2008-08-08
wow thanks worked a charm...
never would have thought of that at all....XD

---

