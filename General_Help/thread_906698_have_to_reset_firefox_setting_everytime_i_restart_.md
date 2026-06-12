---
title: "have to reset firefox setting everytime i restart it..."
date: 2008-08-31
forum: General Help
---

### Post by shredder12 on 2008-08-31
I have hardy installed on my system..
and have firefox 3
the problem is that ..
now suppose i have changed my setting of firefox..
e.g. i have the default page...at the time of opening..
and i have changed the use of backspace to view previous pages..
it will work then..
but when i will restart it..
all the setting would be changed to default..
how do i set them as default..

---

### Post by Zorael on 2008-08-31
It sounds to me like a permissions issue. Close all open firefoxes and then enter this in a terminal; might just do the trick. Replace *<user>* and *<group>* with your user- and groupname. Omit the < and > signs too, obviously.
```
$ sudo chown *<user>*:*<group>* ~/.firefox -R
```

---

### Post by lswb on 2008-08-31
In addition to Zorael's advice also check that you haven't somehow made ~/.mozilla/* files read-only

chmod -R u+rw .mozilla/*

---

### Post by kaibob on 2008-09-01
Here is an earlier thread where a forum user had the same problem. The solution (as suggested by Zorael) is to change permissions on the Mozilla folder:

[http://ubuntuforums.org/showthread.php?t=869545](http://ubuntuforums.org/showthread.php?t=869545)

If by chance that doesn't help, you may want to try creating a new profile by entering "firefox -ProfileManager" in a terminal window. If Firefox runs properly with the new profile, you can copy over your bookmark and any other user files and, after a test period, delete the old profile. 

[http://support.mozilla.com/en-US/kb/Managing+profiles](http://support.mozilla.com/en-US/kb/Managing+profiles)

---

### Post by shredder12 on 2008-09-06
Hye thanks man that worked..

---

