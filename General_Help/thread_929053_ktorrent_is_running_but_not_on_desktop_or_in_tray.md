---
title: "ktorrent is running but not on desktop or in tray?"
date: 2008-09-24
forum: General Help
---

### Post by king james on 2008-09-24
From the command line typing "ktorrent" tells me that it is already running. I can see my network has a heavy load, so it must be downloading and uploading, but I cant see the window anywhere. It is not in my tray either. I recently installed compiz, which probably has something to do with it.

---

### Post by _sAm_ on 2008-09-24
The command **top** will tell you what is running on your system(or with gui; System > Administration > System Monitor and look under the tab Processes). Top will also tell you the PID number for each process. If ktorrent is working you can shut it down with the **kill** command, and then you can restart it(sometimes programs starts without the gui on my pc as well). To kill it run **kill [PID number]**

And by the way, I like htop better then top in the terminal, but you need to install it first with *sudo apt-get install htop* and start it with the command **htop**.

---

