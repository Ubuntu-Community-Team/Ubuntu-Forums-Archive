---
title: "Ubuntu 9.10 install - Unknown job: usplash"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Hamburger493 on 2009-10-31
Hey Everyone, 
I am running a windows xp/ubuntu dual boot, and recently started the Ubuntu 9.10 update from 9.04. During the update, my brother canceled it...Now, everytime i start up ubuntu i get the error message: Unknown job: usplash

I'm thinking this is because my system is half updated? I'm a real linux noobie, any help is appreciated. Thanks in advance. :(

---

### Post by dehcbad25 on 2009-11-17
i have the same problem, except that my computer lost power during the update process. I am hoping someone knows how to fix this since I use the machine as a server.

---

### Post by dehcbad25 on 2009-11-17
doing some research I found that usplash is part of the boot loader? or something like that.
anyhow, pressing ctrl+alt+F1 took me to the promt, where I can login to the system. Great!!
However, I don't have network access, since it seems to be corrupted, but [Hamburger493]("http://ubuntuforums.org/member.php?u=942112") you might try to reinstall the desktop to see if it fixes your problem

---

### Post by dehcbad25 on 2009-11-18
This is all that I did, and I could not fix my system, however, it might help someone else
press ESC at the boot screen to get the option list, and select the recovery mode.
Here you can try to finish installing packages (there is a mode for that)
If it does not work then try:
once in a shell, copy back the source file /etc/apt/source.list 
source.list will have the sources for karmic, but sources.list.save will be the backup copy, so rename sources.list to sources.list.karmic and then copy sources.list.save to sources.list
I did not do this step, and possibly here is where I messed up. I did not do this
then do apt-get update and apt-get upgrade
If this worked, great!!!
you can also try recovering using the CD, and recover a broken system.
In my case, I fixed a lot of the issues, but I still get weird errors when updating the system, so I will re-install

---

