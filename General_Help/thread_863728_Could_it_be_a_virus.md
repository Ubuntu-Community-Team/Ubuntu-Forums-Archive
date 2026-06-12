---
title: "Could it be a virus?"
date: 2008-07-18
forum: General Help
---

### Post by Bruno12 on 2008-07-18
I posted a threat wondering why my password isn't working. Is it possible that a virus (there is one on my computer) has reset my password?
I just turned the computer on and now my password is disabeled, i didn't touch anything...

---

### Post by Sef on 2008-07-18
No.  If there is one on your computer, it is for Windows and will not affect your system.  Mostly likely the wrong password is being typed in, also someone could have changed it, or there's a glitch with in the system.

---

### Post by schauerlich on 2008-07-18
Also, as silly as this seems, you might want to check your caps lock and num lock keys.

---

### Post by cybrsaylr on 2008-07-19
Ubuntu is pretty secure. Does anyone else know your password who may have changed it.

Here's a good read on how Ubuntu stays virus free:

[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

---

### Post by songshu on 2008-07-19
first guess would be indeed the caps and numlock.

second guess, does anybody have physical access to your computer who might have changed it?

third guess, are you running any services that allow you to login remotely? ssh, NX, VNC or things like that?

if it is not the first guess, i would recommend the following.

shutdown the computer NOW!
use a live CD and mount the hard drive to look for the logs
/var/log/auth /home/you/.bashrc those kind of things.

if in doubt, format all and reinstall!!!!!!!



your house can be secured with the best locks available, but if you leave the front or back door open it will not do you any good.

---

