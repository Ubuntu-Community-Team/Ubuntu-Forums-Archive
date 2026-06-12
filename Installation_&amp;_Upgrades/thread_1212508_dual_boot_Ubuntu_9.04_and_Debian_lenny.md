---
title: "dual boot Ubuntu 9.04 and Debian lenny"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by newIsle on 2009-07-13
will another linux distro effect Ubuntu's xorg.conf file and Nvidia drivers when installed on a seperate partition??? they shouldn't right???

---

### Post by mrhobbeys on 2009-07-13
I did this. I found it best to install Ubuntu last as it seems to do a better job of finding and adding OSs to the list. You can always edit the list to add OSs that were missed.

---

### Post by starcraft.man on 2009-07-13
I'm not sure why you'd think that, as long as your installing the root of debian to another partition (for it's root directory) there's no problem. The only way your xorg could be messed up is if you went to the trouble of mounting /etc to a separate partition and then installed debian over it (quite unlikely and not needed).

All files for a distro are kept in their own respective root partitions, so no worries. You can however share home partitions if you made a separate partition for yours and put all your media files in it. Just make sure you have a different username (i.e. maybe put a D. in front to indicate debian). If you used the same username, you'd overwrite the existing home user directory.

I think that's it. I don't know about hobbey's note on GRUB, I've never had trouble with other linux OSes with it, just Windows. If you do, post back here and we can help ya fix it.

---

### Post by newIsle on 2009-07-13
hey thanks starcraft.man, i know what you point out is true, thats why i posted this, i dont understand whats happening,....

ok so i tried installing this flavor of linux (Animux)...

the first problem was the partition i tried to install on was still mounted to Ubuntu, when i installed this linux verision(its actually Xcfe not debian....sorry) and tried to log back into Ubuntu, X-server crashed...so i re-configure -phigh x-server.....I even had to boot a live cd and edit the grub just to log back in...

when i look at xorg.conf nothing that i can see has changed i'll try and recreate again and post

I then um mounted the partion edited fstab, re installed the Xcfe, but the same thing, is it doing something to the xorg.conf ???? I have limited info to post here right now...sorry

i have several dual boot systems set up( all Ubuntu flavors though) i.m not quite sure whats happening here though ....

anyone with some more thoughts???

---

