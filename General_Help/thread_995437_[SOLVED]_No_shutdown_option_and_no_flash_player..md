---
title: "[SOLVED] No shutdown option and no flash player."
date: 2008-11-27
forum: General Help
---

### Post by Dtortot on 2008-11-27
As the title says. When I tried to shutdown my computer a few minutes ago, I noticed the Shutdown option was no longer available, I can lock my screen, hibernate, suspend the system, change user profiles and close my current session but I can't shutdown the system. Is there any way I can see the shutdown option again?

And I tried viewing some vids today on Gametrailers and YouTube but couldn't because it said I didn't have Adobe Flash Player, but I remember installing one of the alternatives but it didn't work, so I then used the file provided by Adobe to install Flash Player on a Linux OS and selected the .deb option, but it still doesn't work. I have rebooted my computer and Firefox and nada. Any clues?

Thanks in advance and please keep it simple with the jargon since I am a new to the whole Linux thing.

---

### Post by binbash on 2008-11-27
for flash player : 

[http://help.ubuntu.com/community/Medibuntu](http://help.ubuntu.com/community/Medibuntu) 

add medibuntu repo to your sources.list and give sudo apt-get install flashplayer-nonfree command.

I dont know the shutdown option since i am not using gnome but for a temporary fix you can use this command to shutdown : sudo shutdown -rh now

---

### Post by Dtortot on 2008-11-27
Thanks a bunch, it sure is a quick fix, but it will work for now.

---

### Post by Dtortot on 2008-11-28
Hmmm... apparently nothing worked, I still can't play flash videos. Nor propperly shutdown my computer.

---

### Post by Dtortot on 2008-11-28
Well the flash player issue is now solved and for a more practical solution regarding the shutdown of my computer I configured the power button to shutdown the computer if pressed. But I would still like a real fix on this.

Thanks.

---

