---
title: "Can't Log In To User Account (Acer Aspire 5733z 12.04)"
date: 2012-05-18
forum: Hardware
---

### Post by kris07 on 2012-05-18
Hi, I was just messing around with a bunch of different things trying to up the sensitivity of my touchpad, and now I can't log in to my account. Not under any of the Gnomes or Unities. Any help with this would be greatly appreciated. I can log in under a Guest for some reason though. It seems that when I try to log in the log in screen resets itself and it's an ongoing process.

---

### Post by Aisteru on 2012-05-19
I've had similar problems. I'm not sure about your situation, but the problem I had was caused by not being able to access my home folder properly. 

Try logging in to tty1 (by pressing ctrl-alt-f1 & typing your user name, etc.) if you can log in there, run ```
ls -alh
``` to check to make sure that the owner is set as your user name & permissions are set to allow the owner read access for all files except for the one called ```
..
```If the owner and/or permissions are set wrong on any of the files, run ```
sudo chown -R user:user .
``` (replacing 'user' with your user name) to change the owner & ```
chmod -R 700 .
``` to change the permissions. Then switch back to the graphic login screen by pressing ctrl-alt-f7, & try logging in again. If that doesn't fix it, the partition that holds your home folder may be too full.

I hope this helps. :-)

---

