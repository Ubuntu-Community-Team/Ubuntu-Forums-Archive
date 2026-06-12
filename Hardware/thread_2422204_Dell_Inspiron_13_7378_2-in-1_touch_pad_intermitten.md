---
title: "Dell Inspiron 13 7378 2-in-1 touch pad intermittently stops working"
date: 2019-07-03
forum: Hardware
---

### Post by oddballmotorsports on 2019-07-03
An annoying problem has arisen for me, every once in a while my touch pad just decides to not work,  A reboot brings it back, it didn't happen after an update, either that or I don't remember.  Anyways,  just the touch pad fails, the buttons still work, and also the touchscreen still works. Just no pointer.  I'm at a loss where to start to diagnose this.  any suggestions?

---

### Post by #&amp;thj^% on 2019-07-03
I would first check this out: [https://www.dell.com/support/article/us/en/04/sln308258/precision-xps-ubuntu-general-touchpad-mouse-issue-fix?lang=en](https://www.dell.com/support/article/us/en/04/sln308258/precision-xps-ubuntu-general-touchpad-mouse-issue-fix?lang=en)
Having multiple touchpad devices running confuses syndaemon.
Also check to just see if this instaled:
```
apt policy touchegg
```
Don't install it just yet, just check.

---

### Post by oddballmotorsports on 2019-07-06
Installed: (none)
  Candidate: 1.1.1-0ubuntu1
  Version table:
     1.1.1-0ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages

so gonna say no?

---

### Post by oddballmotorsports on 2019-07-07
also working through that dell article,  I do have 2 touchpad drivers active,  but I don't have that file listed in that location..  trying to figure out why...

---

### Post by #&amp;thj^% on 2019-07-09
Sorry I had plum forgot about you.
Yep 2Drivers install touchegg now.
```
sudo apt install touchegg
```
Tweak the settings to see if this will disable one.

---

