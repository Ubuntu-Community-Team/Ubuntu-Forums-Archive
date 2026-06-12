---
title: "Export wireless config/drivers/settings?"
date: 2008-09-09
forum: General Help
---

### Post by DarkShadow791 on 2008-09-09
I recently installed Ubuntu inside my existing WinXP install and managed to get my broadcom wireless card to work after about 2 days of tweaking. Now I would like to partition my drive and give ubuntu it's own "real" install. However, I do not know what exactly it was that finally "fixed" my wireless card to get it to work and was wondering if there's some way to export the drivers/config files/settings so I can then import it into a fresh install.

Thanks

---

### Post by DarkShadow791 on 2008-09-10
Anyone? I've had no luck on my own or via irc channels :(

---

### Post by Ayuthia on 2008-09-10
> **DarkShadow791 said:**
> Anyone? I've had no luck on my own or via irc channels :(

If you don't know what you done, you will need to start by checking what drivers your network card is using.  You will need to go into the Terminal and type:
```
lshw -C network
```
Under your wireless card information, you should see a section that mentions about the driver it is using.  It should either say wl, b43-bridge (or something like that), bcm43xx, or ndiswrapper.

If it is b43, you will need to copy the following firmware folders:
```
/lib/firmware/b43
/lib/firmware/b43legacy
```

If it is bcm43xx, you will need to copy the following files:
```
/lib/firmware/bcm43*
```

If it is ndiswrapper, you will need to track down which version of ndiswrapper you are using:
```
ndiswrapper -v
```As for the driver, that is more difficult because the system does not easily keep track of which driver you are using.

The other two files that you will need are:
```
/etc/modprobe.d/blacklist
/etc/modules
```

Of course, if you are using ndiswrapper, if there was a script that you had to create, you will need that also.  Unfortunately, there are many different guides that tell you to do it in different places.  It could be in /etc/rc.local, /etc/init.d, or /etc/modprobe.d/ndiswrapper.

Of course, copying all of this will not necessarily guarantee that you will be able to get your wireless working, but it might be able to help someone get you on the right track.

The key part is to figure out what driver you are currently using.  From there, most likely someone can guide you back in the right direction.

Not really a clear answer, but hopefully it will get some of the things that you will need.

---

