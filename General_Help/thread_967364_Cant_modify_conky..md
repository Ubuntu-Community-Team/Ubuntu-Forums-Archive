---
title: "Cant modify conky."
date: 2008-11-02
forum: General Help
---

### Post by LukeRocksALot on 2008-11-02
hi all,ive been trying to change the look of conky and everytime i do,it keeps on going back to the regular conky look.I have the conky.conf.jz on my desktop open that up and change it around,and hit save,then a window pops up saying "Update the file "conky.conf" in the archive "conky.confg.gz.....i hit Update and it goes back to regular conky,i also tried to hit cancel and it still goes back to regular conky,Any suggestions? Thanks!

---

### Post by WiFi Ed on 2008-11-02
Follow the steps in this thread:

[http://ubuntuforums.org/showthread.php?t=353362&highlight=conky](http://ubuntuforums.org/showthread.php?t=353362&highlight=conky)

You need to put a Conky configuration file in your user directory:
"/home/username/.conkyrc"

The thread will guide you on the path to Conkyness...

---

### Post by LukeRocksALot on 2008-11-02
i tried following the instructions but i got lost after the part you install it,the thread is over a year old

---

### Post by Gauvenator on 2008-11-02
If you already have made a conky config file, you need to copy it to your home directory as .conkyrc

```
$cp /pathtoconky.conf ~/.conkyrc
```

---

### Post by taurus on 2008-11-02
What does your conky.conf.jz look like?  Try moving it to your $HOME directory and renaming it to .conkyrc.

Applications -> Accessories -> Terminal
```
cd Desktop
cp conky.conf.jz ~/.conkyrc
```

---

### Post by LukeRocksALot on 2008-11-02
idk,im so new to ubuntu,i uninstalled conky like 5 minutes ago,idk what to do thx though,also my video cards are getting over 60 C on ubuntu,on xp i get to control my cards fan's to make it 46 C,any chance i can a program to control these temps?

---

