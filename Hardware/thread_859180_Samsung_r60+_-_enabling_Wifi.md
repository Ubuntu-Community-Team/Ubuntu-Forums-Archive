---
title: "Samsung r60+ - enabling Wifi"
date: 2008-07-14
forum: Hardware
---

### Post by Peter_W on 2008-07-14
I've been trying to follow the installation instructions for installing Ubuntu on a Samsung r60+ laptop given by beN..87 at [http://ubuntuforums.org/showthread.php?t=839000](http://ubuntuforums.org/showthread.php?t=839000) , and have managed to get as far as installing the madwifi wireless patch. I get stuck at the instruction to input "modprobe ath_pci" to set the wireless module - I get errors saying the required files can't be found in folder /lib/modules/2.6.24-19-generic/madwifi - however, the folder /lib/modules/2.6.24-16-generic/madwifi (i.e. the difference between the paths is that "19" changes to "16") does seem to contain the files the computer is looking for. What's happened here and how can it be fixed?

---

### Post by beN..87 on 2008-07-14
are you root?

sudo bash
modprobe ath_pci

or -

sudo modprobe ath_pci

---

### Post by Peter_W on 2008-07-17
Sorry for my delayed reply - yes I am root - the computer seems happy to carry out the instruction, it's just that the files it needs don't seem to be where it thinks they are.

---

### Post by beN..87 on 2008-07-17
yeah it seems the patch filename is off ; assuming you have the right patch it is perhaps a bug, or maybe the patch  has been updated and somebody made a mistake; i'm not too sure really how to help but my advice would be to do

cd madwifi
make uninstall
make clean
make
make install

and carry on with the process

if your problem persists - post it in this thread [http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

nicedude is the man for wireless , and his post is where i got the info from so perhaps someone on that thread can figure it out

sorry i can't help more but im sure someone will be able to if you post

---

