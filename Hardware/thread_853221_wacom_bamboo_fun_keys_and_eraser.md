---
title: "wacom bamboo fun: keys and eraser"
date: 2008-07-08
forum: Hardware
---

### Post by breek on 2008-07-08
i've installed the driver and tablet works pretty good on gimp.
...but...
- eraser actually... write... doesn't delete (both sides act the same way)
- i'd like to set the keys like (1) scroll left (2) scroll right (3) zoom in (4) zoom out but i haven't found a guide about it (wacomcpl? how?)


(linuxwacom 0.8.0-3 - xubuntu 8.04)
any ideas?
thanx ;)

edit: ok for the eraser (solved simply selecting the eraser tool using the other side of the pen :D) ... but what about the keys?

---

### Post by breek on 2008-07-08
solved the keys issue too :P
simply executing
xsetwacom set pad button1 "core key left left left left left left left"
xsetwacom set pad button2 "core key +"
xsetwacom set pad button3 "core key right right right right right right right"
xsetwacom set pad button4 "core key -"
when x starts ;)

(of course -> gimp: scroll and zoom; inkscape: zoom; firefox: scroll...)
bye

---

### Post by elmodern on 2008-09-04
That's not working for me. If i do it, whenever i hit the 'configured' key, X crashes. However the commands shown in this [[+]("http://ubuntuforums.org/showthread.php?t=631881")] thread work.

So the question is still alive i guess.

---

