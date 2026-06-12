---
title: "Problems installing"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by Hawk666 on 2009-10-11
Hey everyone, very new to Ubuntu, haven't had any real issues so far, except this one, i've been following [http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127) to install and every time I try to run 
```
sudo make install
```i get this:

```
make: *** No rule to make target `install'.  Stop.
```not sure what the problem is and no that it's something obvious
Nick

---

### Post by rreese6 on 2009-10-11
looks like you are trying to install Kiba-dock.
Tis is not something someone new to linux should try...but if you are bent on installing it (and possibly messing up your system).
Then you need to read the instructions carefully and understand every step. if you don't know what something means in the instructions, DO NOT SKIP IT. Research and study. Basically the error you are getting is from running the make install command that is done after you configure and make a source code package. Evidently you either have not done those steps or  you are not in the correct dirtectory.
A word of advise. if you a new to Linux, stick with installing programs using the "ADD/REMOVE PROGRAMS" software. then graduate to Synoptic later. Installing from source code is not something a new user should attempt unless you are just having fun learning and don't mind reinstalling the complete OS after "experimenting"

---

### Post by mechro on 2009-10-11
To follow on from rreese6's advice why not go for Cairo-dock which is available from Add/Remove?

---

### Post by Hawk666 on 2009-12-05
thanks guys, starting to get a lot more familiar with the terminal, it all looked very confusing at first, me being a windows user and only ever seeing DOS for command line stuff, buts it's gettin easier everyday

---

