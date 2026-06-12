---
title: "external hard disk Packard bell"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by antonio.segalini on 2007-09-25
HI guys

I bought just today an external hard disk packard bell Store and save 3500 with a capability of 500 GB. I have connected this device to my laptop but seems to be a read only unit. How can I do with the use of ubuntu only? i don't have any windows computer to try to format the ext hard disk.

Thank you for every answer

---

### Post by uclalinux on 2007-09-25
NO, you should be able to read and write. 

I believe the problem is that your HD is formated in NTFS, and if so you need to install the package. 
```

sudo aptitude install libntfs-3g0
```

after that you should be able to write to it. 

if that is not the problem then right click on the icon that represents your external HD, and look at it permissions tab, see who owns it and what the settings are. 

If the owner is not your normal user name, then do the following

```
sudo chown "username":"username" "full location address"
```

or  CLick on the link at my footer, and find the section on external Hard drives, it is simple to follow.

---

### Post by antonio.segalini on 2007-09-25
You're right. The owner is root. Sorry but i don't know what i have to write to indicate that driver. And what i have to write if i want that this driver work whit all the users. Thank you very much

---

### Post by antonio.segalini on 2007-09-25
however, if I try to create a folder linux says me that the unit is a read only unit, also if I am the root

---

### Post by uclalinux on 2007-09-27
You need to learn how to change the owner of the drive from root to your user name,  look up "chown" command for linux, 
the command will be something like this

sudo chown "your user name"  "path to drive"   

here is the wiki page for chown [http://en.wikipedia.org/wiki/Chown](http://en.wikipedia.org/wiki/Chown), there is lots of info on the web for this problem just type "change owner of drive" or something to that effect into google, also this forum problem has a over 100 discussions on the same problem.

---

