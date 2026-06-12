---
title: "&quot;trying to resume from /dev/disk/by&quot; Error when booting into Ubuntu"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by Linux4theWin on 2008-12-07
After that my computer battery went emty and my laptop turned off without a normal shutdown.
after that i cannot boot into linux anymore and i get this screen after some loading.
"
Loading. ;please wait...
kinit: name_to_dev_t (/dev/disk/by=uuid/75da5a74-fd14-4eco-973c-b7cf1778b8a
kinit: trying to resume from /dev/disk/by-75da5a74-fd14-4eco-973c-b7cf1778b8a
kinit: No resume image, doing normal boot...
Ubuntu 8.04.1 Linux-320i tty1
Linux-320i login:_
"
It allowes me to to login there but i can never login to desktop or anything.  Only this text screen mode.

What can i do :S  . . . 

Thank you.
Greetings ,
Bjarni

---

### Post by Linux4theWin on 2008-12-07
anyone? :(:(

---

### Post by snova on 2008-12-07
I don't think that error is relevant, or even whether it's actually an error. I've seen it before. It's probably something else.

Try this:

```
sudo /etc/init.d/gdm start
```

It should start the GUI manually. It's a workaround, but somebody else will have to tell you how to fix it permanently.

---

### Post by Linux4theWin on 2008-12-08
> **snova said:**
> I don't think that error is relevant, or even whether it's actually an error. I've seen it before. It's probably something else.

Try this:

```
sudo /etc/init.d/gdm start
```

It should start the GUI manually. It's a workaround, but somebody else will have to tell you how to fix it permanently.

Thanks for trying but it dont work to start this becuse it is "not installed" and if i install it it gives me some "could not install whole pacakade" or something like that. . . 
i think i will just have to format . .

Could this have anything to do with the terminal commands that i did after reading this post ? 
[http://ubuntuforums.org/showthread.php?p=6326186#post6326186](http://ubuntuforums.org/showthread.php?p=6326186#post6326186)

---

### Post by snova on 2008-12-08
Oh dear! Looks like you removed GDM.

Reinstall it:

```
sudo apt-get install gdm
```

Hope this works...

---

### Post by raketten on 2008-12-08
I had the same problem.
I couldt only start the graphic env via startx after
kinit: trying to resume from image bla bla bla
Then I installed the KDE package and rebooted - and voila! The problem is resolved!

Now my problem is: which application is best: GNOME og KDE ??? :lolflag:
/raketten

---

### Post by snova on 2008-12-08
Whichever you prefer...

---

### Post by damis648 on 2008-12-08
You are going to want to do the following to reinstall everything you removed:
```
sudo apt-get install linux-sound-base alsa-utils alsa-base gdm fast-user-switch-apple gdm-guest-session ubuntu-desktop
```
and after that type
```
sudo reboot
``` and you computer will reboot and you should be back to normal.
BTW, that is not an error you posted. That is just a comment stating that the system has not found an image to resume from hibernate, so it will boot normally and not attempt to resume from hibernate.

---

### Post by Linux4theWin on 2008-12-09
[https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148)
I found this and did this  .. .

[http://www.thekip.nl/2007/12/18/kinit-no-resume-image-fixed/](http://www.thekip.nl/2007/12/18/kinit-no-resume-image-fixed/)

and 

This 

sudo apt-get install ubuntu-desktop


> **snova said:**
> Oh dear! Looks like you removed GDM.

Reinstall it:

```
sudo apt-get install gdm
```

Hope this works...

Thank you

> **damis648 said:**
> You are going to want to do the following to reinstall everything you removed:
```
sudo apt-get install linux-sound-base alsa-utils alsa-base gdm fast-user-switch-apple gdm-guest-session ubuntu-desktop
```
and after that type
```
sudo reboot
``` and you computer will reboot and you should be back to normal.
BTW, that is not an error you posted. That is just a comment stating that the system has not found an image to resume from hibernate, so it will boot normally and not attempt to resume from hibernate.

Now my sound is like from a old old radio from World war 1 
it is just . .crap. will
```
sudo apt-get install linux-sound-base alsa-utils alsa-base gdm fast-user-switch-apple gdm-guest-session ubuntu-desktop
```

Fix my sound ?

---

