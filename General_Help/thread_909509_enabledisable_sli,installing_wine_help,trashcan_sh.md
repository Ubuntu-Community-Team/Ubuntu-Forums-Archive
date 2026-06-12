---
title: "enable/disable sli,installing wine help,trashcan shortcut in avant....."
date: 2008-09-03
forum: General Help
---

### Post by LukeRocksALot on 2008-09-03
hey i wanted to know how to enable/disable sli,i have two 9800gtx,and i installed wine but it wont show up in applications tab and,how can i add the trash can to avant?And how can i make it so avant starts when ubuntu starts?Thanks!

---

### Post by LukeRocksALot on 2008-09-03
also is there a way i can get peerguardian2,on ubuntu? or something exactly like it that blocks bad ips

---

### Post by LukeRocksALot on 2008-09-03
bump

---

### Post by LukeRocksALot on 2008-09-04
bump again....

---

### Post by LukeRocksALot on 2008-09-04
please any1?

---

### Post by LukeRocksALot on 2008-09-05
i figured out how to start avant ........

---

### Post by yjwong on 2008-09-05
You could have searched on Google while waiting for replies to your question. Please be patient, the members who give support here are volunteers and thus they also do have other tasks to do.

As for your SLI question, [this thread]("http://ubuntuforums.org/showthread.php?t=523627") for your answer.

Wine is not intended to be run from the Applications menu. You will need to use Wine via the Terminal (Applications -> Accessories). You will probably need to familiarise yourself with the Terminal a little if you haven't done so. The command for Wine on the Terminal is "wine". To start a program using Wine, type this in a terminal:

```
cd "<folder of Windows program>"
wine "<filename of Windows program>"
```

Where <folder of Windows program> is the path to where the program is stored (i.e. /media/sda1/Program Files/Safari), and <filename of Windows program> is the name of the Windows program you want to start (i.e. Safari.exe).

As for adding the trashcan to Avant Window Navigator, go to System -> Preferences -> Awn Manager. On the left pane, click "Applets", look for "Trash Applet" and drag it to the bottom.

Hope this helps.

---

### Post by LukeRocksALot on 2008-09-05
i couldnt find that trashcan applet
heres a pic 
[http://i16.photobucket.com/albums/b15/LukeRocksALot/Screenshot-2.png](http://i16.photobucket.com/albums/b15/LukeRocksALot/Screenshot-2.png)

---

