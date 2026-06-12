---
title: "Oops, what did I do???"
date: 2005-01-24
forum: Installation &amp; Upgrades
---

### Post by ctt1wbw on 2005-01-24
I just rebooted and for some reason, Ubuntu is going straight to a command line login.  I have to login and then type startx for everything to work normally.  What happened?  I downloaded Jabber and some other things for Gnome, but what the heck???

---

### Post by ctt1wbw on 2005-01-24
Update:

When I go to the Computer menu and click Log Out, the options to shut down or reboot are not there anymore.  What is going on?

---

### Post by Quest-Master on 2005-01-24
Post your /etc/apt/sources.list here.

---

### Post by ctt1wbw on 2005-01-24
Okay here it is:

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe  
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

---

### Post by ctt1wbw on 2005-01-24
Okey dokey, here's the scoop.  My system WILL NOT shutdown properly.  The only option I have now under the Log Out action is to log out, but that takes me to a prompt and no matter how many times I type shutdown now, it won't happen.  I even typed shutdown -F and shutdown -P and nothing happened, it acts like it is going to do something, but then stops again at the prompt.  If I type exit, I go back to usr login and password.  X won't even start, I have to type startx.  Man, oh man, what did I do today?  Holy cow!

---

### Post by ctt1wbw on 2005-01-25
Fixed!  I figured out that the GDM was corrupt or something.  I reinstalled it and now everything is hunky dorey again.  :)

---

