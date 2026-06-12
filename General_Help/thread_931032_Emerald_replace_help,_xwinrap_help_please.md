---
title: "Emerald replace help, xwinrap help please"
date: 2008-09-26
forum: General Help
---

### Post by Soldierexile on 2008-09-26
Hello every time i run emerald --replace command in terminal it replaces the them but then i close the terminal and the bar at the top of any of my folders or explorers vanishes. how do i keep the them loaded so that this doesnt happen.

And where can i get xwinwrap. i cant find it. I dont know how to compile the script i keep finding.


i Use Ubuntu 8.04

---

### Post by loomsen on 2008-09-26
either type 
emerald --replace &

or add it to your startups. fusion-icon should work too, as well as emerald --replace as command in ccsm --> window decorations

xwinwrap:
you don't need to compile it, you can simply run it. you may have to make it executable first:
chmod +x /path/to/script/xwinwrap (adjust the path)

and run it for example with:
```

nice -n 15 ./xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- /usr/lib/xscreensaver/glmatrix -root -window-id WID

```

if you dont have xscreensaver installed, install it first.

xwinwrap --help should give you a description of available options to run the video you like.

---

### Post by Soldierexile on 2008-09-26
Thanks alot It works fine now thanks to you:). finaly i dont have to leave that cursed terminal open...lol. 

I got xwinwrap to work but how do i get it to keep the desktop icons on top of the screen? also that doesnt stay open unless i leave the terminal open for it.

* EDIT *

NVM i got winwrap to work without terminal. im fine... Thanks again for all your help

---

