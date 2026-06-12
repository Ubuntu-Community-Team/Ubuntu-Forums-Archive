---
title: "Losing mounted volume on desktop after a restart of  GDM"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by DarkSilver on 2005-06-14
Hello,

**1/**
The first time I boot since my new windows partition were mounted, I could see them on my desktop (they are in fstab)
When I plug my usb key, I could see it too !
Everything was fine !
(I have checked to show volume on desktop)

But after a few reboot, I didn't see them anymore...
I have to do a:  sudo /etc/init.d/dbus-1 restart to see them again ...
And it was not only on desktop! 
It was also in /media (I mount them in /media), so I didn't see them in "Computer" (computer:///) anymore too...
Because theses devices were not mounted at all !!!

But If I do a restart of dbus-1... and I plug my usb key again, It is not mounted and so not shown too !!

Well, How does it work ????
How can I do a clean restart of dbus-1 whithout having these troubles??

**2/**
Another point is when my usb key is mounted and I logout, I lost the mount !!
I saw in the process a dbus-launch --exit-with-session..
So I think this is it 
but why ???
I don't see why when I go to console (CTRL+ALT+F1) I have to lost my usb key ???
I think when it is mounted, it is mounted until the restart or a manually unmount ! (and not for X session only)
So what can I do to prevent this ?

**3/**
another strange thing
The name of mounted volume !
I mount (in fstab) my 2 windows partitions in /media (/media/C and /media/D)
If is is mounted at boot, I show them in My Desktop and My Computer with their name : C and D
but if i manually mount them, I see : "19GB Hard Drive: 19G Media" in computer:///, or something like this and not the name ??
I I do a sudo /etc/init.d/dbus-1 restart, the correct name are shown again (C and D) and I have icons on desktop
but if I do a gdm restart (well, a logout and a login), they are not shown in Desktop anymore but the name is "19GB Hard Drive: 19G Media" again ...
How does it work too ??
How can it be alwayd mounted, always shown in Desktop and in computer:/// with correct name ?

thx
(and sorry for my bad english)

---

### Post by DarkSilver on 2005-06-14
anyone ?

I think it is a general probem and it concerns a lot of us...

---

