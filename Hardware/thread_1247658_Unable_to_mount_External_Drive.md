---
title: "Unable to mount External Drive"
date: 2009-08-23
forum: Hardware
---

### Post by drifter2502 on 2009-08-23
Suddenly and after using my OMEGA external drive for over a year my Ubuntu 8.04.1 is failing to mount it with the following error :-

'mount_ point cannot contain the following characters:newline,G_DIR_SEPARATOR(usually/)'

I may have installed updates prior to the failure and I did install wine hoping to access some old Windows apps on the external but took it off again because I could not mount my External Drive. Now I am panicking because I have loads of files on there including my wifes photographs! I must fix this before she gives me absolute s..t.

The external is a 120GB v(FAT32) Mount Point/media/OMEGA DRIVE. Help!!

---

### Post by drifter2502 on 2009-08-24
I solved my problem here,,,,[url]https://answers.launchpad.net/ubuntu/+question/37506/
`I went to ubuntu forums and found archives of people that had the exact same problem. Tuned out all you have to do if you are receiving this message is go to your home folder, click view , click on show hidden files , open the .gconf folder and follow this path /system/storage/volumes until you find the folder that contains your device and move it to the trash , unplug your device and reboot. When you plug it back in it should mount . tombo!'

---

### Post by andrew2269 on 2009-08-24
I am trying to Ubuntu on my external harddisk but don't know It is giving me error . I think I found the solution from this post. Thanks for great answer

---

### Post by drifter2502 on 2009-08-25
Ok, you may want to bookmark this too if you have never gone there..[https://answers.launchpad.net/ubuntu/](https://answers.launchpad.net/ubuntu/)

---

