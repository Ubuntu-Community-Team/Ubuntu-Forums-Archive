---
title: "Sony Clie Frustration"
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by Permafrost91 on 2006-04-13
For the life of it, I am not able to set up my Sony Clie (PEG TJ-37) to sync through gnome-pilot (or jpilot as some had suggested). gpilotd-control-applet hangs on identification of the user during setup. I was able to sync it with KPilot a while ago but I don't want to install KPilot now (would like to keep it all Gnome-apps).

I probably have read every thread in this forum relating to this and have followed any and all advice. If anyone knows how to get this sync to work, please help me out.

---

### Post by dolphin_1 on 2006-10-24
I'm having similar troubles with my PEG TJ-35, but I haven't tried in a few months. Can you send me some of the posts you have tried so I can give them a go.  I'll let you know how it goes.

---

### Post by eldragon on 2006-10-30
ok, im having this problem with a sony clie t665c

im going crazy about it. i cant believe syncing a palm could be so painful. i thought switching from dapper to edgy would solve this issue. but......it doesnt seem to be the case. ive tried every post about palms in the formus too. it simply doesnt work. i'll probably be building a irda port this week.  and be done with it.

UPDATE: i came across this link, in spanish, but instructions are there.....considering USB support is enable on ubuntu. i skipped that part. maybe i shouldnt have, but it worked ;)

[http://www.linuca.org/impresion.phtml?nIdNoticia=122](http://www.linuca.org/impresion.phtml?nIdNoticia=122)

the three steps i followed were: as root, do the following:

    # mknod /dev/ttyUSB0 c 188 0
    # mknod /dev/ttyUSB1 c 188 1
    # chmod 666 /dev/ttyUSB*

that got me syncing. just for the record: using edgy eft.

now, if only i could have this done during startup.....anyone?

---

### Post by wastrel on 2006-11-02
There is a problem with Palm USB support in Dapper that makes USB sync very erratic.  Sometimes it works!  Usually it doesn't!

Thankfully this is fixed in Edgy and now we just have configuration problems to overcome in order to get Palm OS talking with Linux.  

See this post for help if you can't get sync working using the /dev/pilot port:  [http://www.ubuntuforums.org/showpost.php?p=1690296&postcount=7](http://www.ubuntuforums.org/showpost.php?p=1690296&postcount=7)

Good luck!

---

### Post by eldragon on 2006-11-02
> **wastrel said:**
> There is a problem with Palm USB support in Dapper that makes USB sync very erratic.  Sometimes it works!  Usually it doesn't!

Thankfully this is fixed in Edgy and now we just have configuration problems to overcome in order to get Palm OS talking with Linux.  

See this post for help if you can't get sync working using the /dev/pilot port:  [http://www.ubuntuforums.org/showpost.php?p=1690296&postcount=7](http://www.ubuntuforums.org/showpost.php?p=1690296&postcount=7)

Good luck!

your the man wastrel. now i dont need to do anything anymore, it even works with gnomepilot, which is much nicer than jpilot. next stop: conduits for thunderbird which i like much more than evolution.

---

