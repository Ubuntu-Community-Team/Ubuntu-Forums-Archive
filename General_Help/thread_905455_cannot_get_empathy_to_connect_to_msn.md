---
title: "cannot get empathy to connect to msn"
date: 2008-08-30
forum: General Help
---

### Post by markp1989 on 2008-08-30
Im trying to install ubuntu mobile on my eee. all good so far, except that i cannot get empathy connect to msn, i have installed telepathy-butterfly, which i think should allow me to connect to msn. 

tried adding an account to empathy, and i get an error saying 

"msn0 
Network Error
edit account"

anything i can do? 

thanks markp1989

---

### Post by sexcopter on 2008-09-11
Speaking from my own experience, this is an issue with python-msn. There is a proposed update, which fixes this problem for me.

This is the bug report:
[https://bugs.launchpad.net/ubuntu/+source/pymsn/+bug/255307](https://bugs.launchpad.net/ubuntu/+source/pymsn/+bug/255307)

I believe it should be moved from proposed to normal updates some time soon, so you could just sit tight and wait for the update to come. If you want it now, you need to enable proposed updates:

[https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

If you do this, I suggest you be careful with other proposed updates. They have not been thoroughly tested and may cause instabilities!


James.

---

### Post by WhiteHorse on 2008-11-13
Same problem here with Empathy 2.24.0

It worked with the original package installed from the Ubuntu repos but then I added the repos from empathy and now MSN doesn't want to work. sigh...

---

### Post by o1e9 on 2010-06-12
It seems the problem happens sometime after back from hibernate.

---

### Post by Rebootkid on 2010-08-13
Quick and dirty work-around to get reconnected:

open up a console and type

killall telepathy-butterfly 

Then, reconnect to MSN.

It'll probably need to be done again after a reboot, but it'll at least get you back chatting.

---

### Post by amishphysicist on 2010-10-19
Workaround worked for me! Thanks!

---

### Post by onemanclapping on 2010-10-21
I've tried everything in here and still can't find a solution... please check out my thread: [http://ubuntuforums.org/showthread.php?p=10004613](http://ubuntuforums.org/showthread.php?p=10004613)

Thanks.

EDIT: SOLVED! [http://ubuntuforums.org/showpost.php?p=10003289&postcount=17](http://ubuntuforums.org/showpost.php?p=10003289&postcount=17)

---

### Post by CaptainMark on 2011-01-07
brilliant, this has been a problem for a while for me, this second fix worked great

---

