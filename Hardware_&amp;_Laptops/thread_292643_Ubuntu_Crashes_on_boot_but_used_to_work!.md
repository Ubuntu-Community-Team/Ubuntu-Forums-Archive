---
title: "Ubuntu Crashes on boot but used to work!?"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by L2wis on 2006-11-04
Hey all, i recently installed ubuntu 6.06 onto my laptop no problems. 

Was running fine, i also installed automatix2 and bits and bobs from that. Well now the system won't boot up. It **goes all the way up2 the part where the login screen should appear but it fails and leaves a black screen with an underscore '_' in the top left corner.**

It will boot into recovery mode, but i've no idea what to do in there to fix it :/ Any help on this would be superb!

Regards

Lewis

---

### Post by bishop71 on 2006-11-04
I'll give it a try.

(Based on experiences with old s3 video card.)

If your desktops config file has been corrupted this may help.

Start with recovery mode.

go to /etc/X11/ directory:
cd /etc/X11

Check if you have a backup of xorg.info file
ls

If you don't I'm afraid I can't help...:( 

If you do, f.ex. xorg.conf.1 or xorg.1 found in that dir you can try:
cp xorg.info xorg.bak
sudo cp xorg.conf.1 xorg.conf

And reboot...
sudo reboot

--bishop71

---

### Post by bishop71 on 2006-11-04
Oops. Sorry:

cp xorg.conf xorg.bak
NOT cp xorg.info xorg.bak

--bishop71

---

### Post by L2wis on 2006-11-04
the only file i had in there was xorg.conf :S

---

### Post by L2wis on 2006-11-05
still got this problem guys/gals :( please help!

---

### Post by schorsch on 2006-11-05
Have you tried this??

```
sudo dpkg-reconfigure xserver-xorg 
```

... even if it seems to be silly, copy your /etc/X11/xorg.conf somewhere else before and check for differences if X is starting up again.

---

### Post by L2wis on 2006-11-05
hey, i've just gone through the set up, i hadn't tried it... fingers crossed

edit: okay this time it seemed like it almost worked however an error popped up this time which says: fatal screens error: No screens found f"

edit: After reconfigurating a few times i found what made it work was setting the accurate screen settings which can be found here for an IBM T21 :D

[http://homepages.inf.ed.ac.uk/mvanross/t21.html](http://homepages.inf.ed.ac.uk/mvanross/t21.html)

Fixed now. Regards! All!

---

