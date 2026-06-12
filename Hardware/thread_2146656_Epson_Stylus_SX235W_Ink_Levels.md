---
title: "Epson Stylus SX235W Ink Levels"
date: 2013-05-19
forum: Hardware
---

### Post by aquascrotum on 2013-05-19
Hi - just checking is there any application or other way to monitor ink levels on the Epson Stylus SX235W printer using 13.04?

I've seen this thread [http://ubuntuforums.org/showthread.php?t=1970513]("http://ubuntuforums.org/showthread.php?t=1970513") that refers to being able to monitor levels from a network page, however I can't network the printer as it seems it can only connect via WPS which has been disabled on my providers router (BT).

Have also tried MTINK (from pre 2009?) however this doesnt have my printer listed and it doesnt detect it automatically.

I chose an Epson printer as it seemed to have all round decent Linux support, its a shame this fairly basic funtionality doesnt seem to be readily available?

---

### Post by Mark Phelps on 2013-05-19
I'm able to use mtink on a fairly new Epson Artisan 730 -- so I know it works with printers newer than 2009.

You do have to play around with it to find the printer -- and running it using "gksudo" works the best.

---

### Post by aquascrotum on 2013-05-19
Solved.

Need to run sudo modprobe usblp for it to work.

Sudo modprobe usblp
Sudo mtink
sudo modprobe -r usblp

After that it picked up the printer automatically.

How would I write a script to make this work as a one click operation?  Its on my Dads PC who isn't going to start going into Terminal etc.

---

