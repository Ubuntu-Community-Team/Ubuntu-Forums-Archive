---
title: "sound card not detected out of the sudden!!!"
date: 2010-11-30
forum: Hardware
---

### Post by Draugen777 on 2010-11-30
Hey guys...i am running Ubuntu 10.04 on an hp g62 laptop... so far i had no problems with sound, or any problem i encountered i managed to fix by doing a bit of googleing...

The thing is almost an hour ago i installed the new updates (as i usually do when there are updates), did the necessary restart, and now ubuntu doesn't detect my soundcard!!! and also i can't use alsamixer... when i write the command in the terminal i get the message no such file or directory... please someone help!!!! i really don't want to uninstall and reinstall the whole OS!!! I've already spent so many hours customizing it!!! please please someone help!!!

---

### Post by Draugen777 on 2010-12-01
no one? :(

i've been searching in forums after i posted the thread here, and still cannot find a solution...
last one that looked helpful was this one: [http://art.ubuntuforums.org/showthread.php?t=1527340](http://art.ubuntuforums.org/showthread.php?t=1527340)

didn't change anything though...
please if someone can help i'd really appreciate it!!!

---

### Post by The Stinger on 2010-12-01
I've got the same problem.
Also happened after an update.

---

### Post by Draugen777 on 2010-12-01
I could not find any solution, so i just re-installed ubuntu... :(
just hope it doesn't happen again...

---

### Post by mastablasta on 2010-12-02
did you have your ALSA upgraded? If so, then updates will mess it up and make the sound not working propperly. it happened on my computer. great updates BTW....
 
if not perhaps you could just try to do alsa upgrade/install and it should solve your porblem.

---

### Post by Draugen777 on 2010-12-02
I did upgrade ALSA to version 1.0.23 because the sound was not working anyway when i first installed ubuntu. It was not just a sound problem, the system could not detect my soundcard.

---

### Post by mastablasta on 2010-12-02
as mentioned one of updates downgraded ALSA (to 1.0.22). i upgraded it (again) to 1.0.23 and now it all works - again.

---

### Post by chriswillmorris on 2010-12-05
I am also experiencing this issue. My Alsa version seems to be at the 1.0.23 version, but maybe it was rolled back without the version # actually updating. I'll try an uninstall/reinstall of Alsa and see what that does.

---

