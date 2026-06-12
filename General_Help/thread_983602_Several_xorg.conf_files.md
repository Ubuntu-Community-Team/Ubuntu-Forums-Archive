---
title: "Several xorg.conf files"
date: 2008-11-15
forum: General Help
---

### Post by i-am-me on 2008-11-15
I was going to modify my xorg.conf file to try to get compiz working again (it stopped working a week or so after hardy was released) and I found 4 different files:
```
/etc/X11$ ls xorg*
xorg.conf  xorg.conf.1  xorg.conf.dist-upgrade-200810142242  xorg.conf.failsafe
```
and I have no idea which to modify (or rather, screw with). Do I combine them all in one file or just ignore some? I've attached them (the txt extension was so the upload would accept it as a valid filetype).

---

### Post by taurus on 2008-11-15
Xorg.conf is the official one.  Xorg.conf.1 is a backup copy.  Both xorg.conf.dist-upgrade-200810142242 and xorg.conf.failsafe need no explanation since you probably could guess what they are.  However, it's also a good idea to look at the date/time that each file was created.

```
ls -la /usr/X11/xorg*
```

---

### Post by i-am-me on 2008-11-15
I was looking at them earlier and saved while exiting out of habit so checking the time is useless now. Even though xorg.conf is the official one, it has almost nothing in it (which is the main cause of my confusion).

---

### Post by taurus on 2008-11-15
Did you use gksudo gedit to look at /usr/X11/xorg.conf?  Next time if you want to look at a file, use more or less instead of opening it a text editor.  

if xorg.conf is empty, then perhaps you need to look at the backup copy, xorg.conf.1.

---

### Post by i-am-me on 2008-11-15
It's not exactly empty, it just doesn't have much in it. I'll back up the current one somewhere and copy the xorg.conf.1 (which has quite a bit) to it and see if it works.

**Update:** Using the dist-upgrade backup got compiz working again. Thanks.

---

### Post by ramaswamyps on 2008-11-16
sudo dpkg-reconfigure -phigh xserver-xorg

console login and run above command.
when X works ok delete all other xorg.conf1234 etc files.

---

