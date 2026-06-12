---
title: "Dell Inspiron 6000 no wireless..."
date: 2005-08-30
forum: Hardware &amp; Laptops
---

### Post by Waxer on 2005-08-30
Hello all, a bit of a noob here, used to windows device manage, I got no wireless on my Dell, works OK in Win XP, I looked at the guides at [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/) but couldn't follow them, I'm afraid I need a simple guide to configuring hardware, if anyone can help, thanks!

---

### Post by dbindner on 2005-12-16
I can't promise that it will work for you, but my success story is at:

[http://ubuntuforums.org/showthread.php?t=104503&highlight=inspiron+6000+wireless](http://ubuntuforums.org/showthread.php?t=104503&highlight=inspiron+6000+wireless)

The short of it is that you'll probably need to use ndiswrapper to get going.

---

### Post by tmartindub on 2005-12-19
You may as well give up if you have a Dell card.  I tried everything I could find and Broadcom chips will NOT work.  I am amazed that these implementations do not provide drivers and wizards to get things like this going.  If Linux will replace Windows, they better get on the move.

---

### Post by Vorian on 2005-12-19
[QUOTE=Waxer]Hello all, a bit of a noob here, used to windows device manage, I got no wireless on my Dell, works OK in Win XP, I looked at the guides at [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/) but couldn't follow them, I'm afraid I need a simple guide to configuring hardware, if anyone can help, thanks![/QUOTE]

Two things.  One there is a bug where your wifi led will not work on your inspiron 6000 while using ubuntu... no big deal just FN F2 to turn it on/off

The second is you either have a intel pro b/g or a/b/g card.  Both of these are supported by Hoary.  When using Hoary, I used the terminal to connect manually to any wireless AP.  

First thing you want to do is try to see if your wifi is on..

In a terminal use #sudo iwlist eth1 scanning

If your wifi is on, you will see your router.  

Second thing to do is manually set your AP mac address

#iwconfig eth1 ap (what ever your ap mac address is)

Next connect to your router

#iwconfig eth1 essid (what ever your router name is)

I diabled my wep key b/c i live in the boondocks of Ohio, but if you have a key the code is

#iwconfig eth1 key s:passphrase

then

#dhclient eth1

and boom!  your in.  

Just as a side note, if you upgrade to Breezy this will not be a problem.  It is super easy in Breezy!

Have Fun! :-)

---

