---
title: "Dragging Files to Ipod Seems to Work, But Cant Find on Ipod?"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by Nick Wilson on 2007-01-15
Dragging some podcasts i downloaded with ipodder to the ipod seems to work, I can even double click them and they play just fine, but when i eject the ipod i cannot locate them on the ipod?

I have tried putting them in the 'Music' folder, but that does not work either. 

Anyone have any pointers on this?

thanks

---

### Post by Paul41 on 2007-01-15
I use banshee with my iPod so this may not apply. When I drag files to the iPod they look like they are on, but they aren't really there until I hit the synchronize button. I don't know if you have something like this with what you are using or not.

---

### Post by netztier on 2007-01-15
> **Nick Wilson said:**
> Dragging some podcasts i downloaded with ipodder to the ipod seems to work, I can even double click them and they play just fine, but when i eject the ipod i cannot locate them on the ipod?

I have tried putting them in the 'Music' folder, but that does not work either. 

Anyone have any pointers on this?


You can drag files or directories of whatever kind to an iPod it and they'll be stored to the iPod the exact same way as to any other USB drive. 

For music, an iPod works differently. Files you want to appear as music on your iPod need to be registered in the Pod's internal database. That's what **gtkpod** and it's associated libraries take care of. 

So you'll have to install **gtkpod** (or another application that uses the libraries) via Synaptic and use it to sync your files with the iPod.


best regards

Marc

---

