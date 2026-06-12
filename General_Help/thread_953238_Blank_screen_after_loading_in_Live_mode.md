---
title: "Blank screen after loading in Live mode"
date: 2008-10-19
forum: General Help
---

### Post by StarryKnight on 2008-10-19
Hello all, this is my first post here... well i recently got myself Ubuntu 8.04 LTS for me, and am going thru some problems which i need to solve to start using the gr8 os...

Whenever i boot using the live cd mode; most of the times it ends up with a blank screen after the loading screen.

The first time i selected acpi=off, and it successfully got to the desktop.

The second time it ended up with the blank screen even after selecting acpi=off; after trying many times, i selected safe graphics mode too and was successful again..

One peculiar thing i notice is that my c: is labeled as '21GB media' and not the usual labels like on my other drives... Has this got to do anythin with the behavior?

I searched for it in the forum n google; there wasn't anythin here, maybe i dint search right, but i found this page on goog [http://ubuntuforums.org/archive/index.php/t-427834.html](http://ubuntuforums.org/archive/index.php/t-427834.html) (ya its from the archives here :))

M running a p4, with 1.2Gb of RAM, and ya its a compaq too...:mad:

---

### Post by jerome1232 on 2008-10-20
That has nothing to do with your problem

Linux doesn't use single letters to designate partitions. they get device assigments and are mounted into the file system.

like this
first disk
sda1 first partition
sda2 second partition

second disk
sdb1 first partition
sdb2 second partition

sda1 mounted at /  (this would be like c: in windows)
sda2 mounted at /home  (so if you opened up the /home folder it would be like going to d: in windows) and etc... hopefully that gives you an idea.

---

### Post by StarryKnight on 2008-10-20
And now i tried again and it booted successfully without modifying any options... and am even posting from there just now. :)

The desktop effects are just so smooth and utilize so less resources...!

The only thing i changed when booting this time was that i switched off my network connection... the blank screen was very short lived (~2 secs) this time... M even more confused now :D...

Thx for the reply jerome, ya i understood what u told bout the hdds...

I'll now just look around in the os before i again try and reboot to see what happens.

---

### Post by StarryKnight on 2008-10-20
Well after making myself familiar to it, i turned it off and the rebooted into livecd mode, and it got through again! :) This time too i had the lan cable out... and it worked again..

all my hardware works perfectly with it, so now m thinking of installing and dual booting with xp...:guitar:

---

