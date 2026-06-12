---
title: "udev, rights and automount..."
date: 2013-11-08
forum: Hardware
---

### Post by martin-peter-just on 2013-11-08
Hey,

I'm new to Ubuntu and I need your help. 

I created udev rules for plugin and unplug of usb sticks.
They seem to work, because I tried to let the rules make symlinks and they were built.

The rules run a script. 
In this script I creat a logfile and the stick I plugged in should be mounted.
But the only things that happens are that something is written into my logfile and the stick gets mounted by automount.
I don't get it because I disabled automount in dconf...

If I started the script manually I got: "mount: only root can do that".
So I tried this: [http://askubuntu.com/questions/185718/allow-non-admin-users-to-mount-drives-via-nautilus](http://askubuntu.com/questions/185718/allow-non-admin-users-to-mount-drives-via-nautilus)

Now I don't know how to continue.

Would appreciate your help. 

Greez :)

---

