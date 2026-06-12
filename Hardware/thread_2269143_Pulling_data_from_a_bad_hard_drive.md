---
title: "Pulling data from a bad hard drive"
date: 2015-03-13
forum: Hardware
---

### Post by captianirish on 2015-03-13
hey guys, as you can tell from the title i am pulling data from a bad drive, but i was wondering. is it possible to have Ubuntu skip the bad files (input/output error) but when all is said and done to have it create a log with name and location of all file that where not able to be transferred? if this was asked already i am sorry. i'm at work and didn't have much time to search, and its odd enough Google doesn't come up with anything with what i typed. ty all for your time.

---

### Post by rioguia2 on 2015-03-13
Logging sounds like ddrescue (sudo apt get install ddrescue)

It also sounds like you should consider installing safecopy and testdisk.

---

### Post by captianirish on 2015-03-13
ok cool. the hdd mounts fine. but like i said alot of files with input output error. grabbed ddrescue but looks terminal based and i am still a novice at terminal commands. all i want to do is copy data from the drive to my external, and have a log of the files that failed/ were skipped.

i am going to look into safecopy and testdisk soon

---

### Post by rioguia2 on 2015-03-15
> **captianirish said:**
>  grabbed ddrescue but looks terminal based and i am still a novice at terminal commands.n


there is a gui project discussed at [http://www.ubuntugeek.com/ddrescue-gui-a-python-script-to-make-it-easier-to-use-ddrescue.html](http://www.ubuntugeek.com/ddrescue-gui-a-python-script-to-make-it-easier-to-use-ddrescue.html)




**Install DDRescue-GUI in ubuntu**

 Open the terminal and run the following commands
 [INDENT]sudo add-apt-repository ppa:hamishmb/myppa
sudo apt-get update
sudo apt-get install ddrescue-gui

[/INDENT]

---

