---
title: "Strange issue when launching startx from getty"
date: 2008-10-02
forum: General Help
---

### Post by Mamono on 2008-10-02
I have a very strange issue that has me baffled.  I have a kiosk system I've created which is PXE booting into Ubuntu.  I have completely stripped it out and am using jwm as my window manager.  It boots up fine and starts X from my getty command in /etc/event.d/tty6 like so:

exec /sbin/getty 38400 tty6 -n -l /usr/bin/kiosk

My X is setup to launch jwm and then Firefox in /etc/X11/xinit/xinitrc like so:

xset s noblank &
xset s 0 &
jwm &
/usr/bin/firefox

When I boot this from the hard drive it all works fine.  But, when I boot from PXE I have a strange problem where X starts but Firefox will not load unless I hit "ctrl-alt" after about 30 seconds.  I've let it sit for five minutes and it doesn't load but it starts as soon as I hit "ctrl-alt", very strange.  My script to launch X looks like this:

#!/bin/bash
su - kiosk -c startx

Anyone have any idea what the significance of "ctrl-alt" would be?  That is all I hit, just those two simultaneously, then it works properly.  I discovered it completely by accident when I went to hit ctrl-alt-backspace to kill X to troubleshoot why Firefox isn't loading.  Hitting them by themselves doesn't do it, neither does one then the other.  

Help!!!

Thanks

P.S.  In case it matters this is using an older serial LCD touchscreen interface and the keyboard and mouse are connected, but not accessible to users.  I have the elographics drivers installed and they are functioning properly.

---

### Post by Mamono on 2008-10-03
I don't know if anyone has even looked at this, but I have some more info.  First off, it will come up if I hit any two keys within 15 seconds.  Second, if I hit ctrl-alt-backspace and let it respawn, every other time it will load up fine.  On the times it doesn't, sometimes it exhibits the same behavior, sometimes I have to kill X again and it comes back.

Here are some additional troubleshooting steps I have done:

Booted up without the keyboard and mouse plugged in
RESULT:  Same behavior, Firefox loaded as soon as I plugged the keyboard in and hit a couple keys (I waited a little bit after plugging it in to see if the plugging in of the keyboard would trigger it to work)

Disabled the keyboard and mouse drivers in xorg.conf
RESULT:  Same behavior

The next thing I am going to try is making a custom kernel and initrd to boot off of with PXE to see if that changes anything.

---

