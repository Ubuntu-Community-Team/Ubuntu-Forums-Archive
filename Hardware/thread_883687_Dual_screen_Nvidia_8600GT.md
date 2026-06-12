---
title: "Dual screen Nvidia 8600GT"
date: 2008-08-08
forum: Hardware
---

### Post by rw_mott on 2008-08-08
Hi,
I can't manage to get my second monitor up and running with ubuntu. 
I have installed the nvidia drivers and as instructed in other threads tried to enable twin view but when I do this it tries to turn the 2 monitors into one huge screen and makes the card go very slowly. I'm looking to set it up with 2 separate screens. 

When I try and use X screen it will not save to the X configuration file saying "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'." 

any ideas what I could do to activate the 2nd screen?

thanks

otherspec
q6600 2.4ghz quad core
4gb ram
250gb sata HD

---

### Post by Mintsoft on 2008-08-08
> **rw_mott said:**
> Hi,
I can't manage to get my second monitor up and running with ubuntu. 
I have installed the nvidia drivers and as instructed in other threads tried to enable twin view but when I do this it tries to turn the 2 monitors into one huge screen and makes the card go very slowly. I'm looking to set it up with 2 separate screens. 

When I try and use X screen it will not save to the X configuration file saying "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'." 

any ideas what I could do to activate the 2nd screen?

thanks

otherspec
q6600 2.4ghz quad core
4gb ram
250gb sata HD

It's having problems saving that file because you need to be root to write to /etc, so use sudo or gksudo to open the program you used to open it. Generally for 2 screens, you just turn off twinview, that way you have 2 seperate X screens, although you won't be able to drag things between screens!

---

