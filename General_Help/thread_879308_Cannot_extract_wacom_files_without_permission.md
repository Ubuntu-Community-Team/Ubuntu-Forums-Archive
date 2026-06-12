---
title: "Cannot extract wacom files without permission"
date: 2008-08-03
forum: General Help
---

### Post by blackbyron on 2008-08-03
Hello, I'm trying to extract linuxwacom 0.8.9-3 to /usr/src.  But it won't let me extract it without the permission, I tryed to go to users settings, no luck.  I need to get the stylus enable.
I used [http://wiki.linuxquestions.org/wiki/Tc1100#Onscreen_Keyboard_at_Login](http://wiki.linuxquestions.org/wiki/Tc1100#Onscreen_Keyboard_at_Login)  to follow directions.

Anyhelp would be great.
Thanks

---

### Post by rainwalker on 2008-08-03
Did you use "sudo" in the command?

---

### Post by blackbyron on 2008-08-04
Thanks for the reply, Yes I did, and it still won't work.

---

### Post by blackbyron on 2008-08-05
bump

---

### Post by Paradoxalley on 2008-08-05
have you added your username to the "src" group?
assuming that your username is "blackbyron" (change blackbyron to reflect your actual username)
```
sudo adduser blackbyron src; chown -R root:src /usr/src
```

let us know if it still isn't working after this...

---

### Post by blackbyron on 2008-08-06
Yep tried that before I post the thread.  It loads so many files after I typed it and everything shows the error "Operation not permitted".

---

### Post by blackbyron on 2008-08-07
bump

---

### Post by blackbyron on 2008-08-08
bump

---

### Post by blackbyron on 2008-08-08
Update: ok I think I got it working because all I did is put the password back in login, and bam.  I wil give you guys update if my problem still exists.

---

### Post by blackbyron on 2008-08-08
Update: How do I apply a patch for "wacom.patch", it says in wiki:
Apply the TC1100 stylus buttons patch (which should be saved in your home directory with the filename "wacom.patch"), and then run configure:
and also, told me to put
"cd /usr/src/linuxwacom-0.7.8-3
patch .pl < ~/wacom.patch
./configure"  in the terminal.

But my wacom is 0.8.0-3

Where do I find the wacom 0.8.0-3 patch?

Thanks :)

---

### Post by blackbyron on 2008-08-12
bump

---

### Post by blackbyron on 2008-08-23
bump ?

---

