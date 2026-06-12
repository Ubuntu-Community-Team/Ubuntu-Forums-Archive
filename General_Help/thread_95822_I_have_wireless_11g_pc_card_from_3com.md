---
title: "I have wireless 11g pc card from 3com"
date: 2005-11-27
forum: General Help
---

### Post by GGINIS on 2005-11-27
I have wireless 11g pc card from 3com,  from that they write to me
they are for XP, it exists software  for ubundu?  that, where I can
find?

---

### Post by Randy Sparks on 2005-11-27
Rather luckily, I wrote about getting this to work just a few days ago:

[http://www.ubuntuforums.org/showthread.php?p=519704#post519704](http://www.ubuntuforums.org/showthread.php?p=519704#post519704)

---

### Post by ofek on 2005-11-27
You need to install ndiswrapper-utils and probably gui for it for the ease of use.
Write this two lines in terminal: ```
sudo apt-get ndiswrapper-utils
sudo apt-get install ndisgtk
```
After that ull need to install your driver through the ndiswrapper gui tool (should be in one of the menus, i'm not sure which because i don't use the gui too often).
When you are finished with that you should remove the prism54 module because it masses up ndiswrapper(atleast for this card) by typing this in terminal:```
sudo modprobe -r prism54
``` and then if you didn't already do it you should type:```
sudo modprobe ndiswrapper
```
The card should now light up and under System>>Administration>>Network you could configure it.
One last thing, if you want the internet to start on boot you should add prism54 to the hotplug blacklist.
Hope this helped you atleast this is how I got my 11g card to work.
There is another thread on this subject and it should help you:[http://www.ubuntuforums.org/showthread.php?t=94898]("http://www.ubuntuforums.org/showthread.php?t=94898)

EDIT:Randy already posted... oops...

---

