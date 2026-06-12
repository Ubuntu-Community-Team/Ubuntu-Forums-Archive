---
title: "Amarok can't connect to iPod"
date: 2005-12-11
forum: Hardware &amp; Laptops
---

### Post by PheonixRising on 2005-12-11
I have Amarok 1.4 running on Breezy, and for some reason, it's not detecting my fourth-gen Photo iPod! Help! (It says :" Sorry, you do not have a surpported portable music player")

---

### Post by 23meg on 2005-12-11
Do you have the "ipodslave" package installed?

---

### Post by PheonixRising on 2005-12-11
Yeah, I installed it from Synaptic. Is there something else I need to do to make it work?

---

### Post by PheonixRising on 2005-12-11
Also, if it matters, I installed amarok using [this]("http://www.ubuntuforums.org/showthread.php?t=80492&highlight=amarok") method.

---

### Post by ltmon on 2005-12-11
Your ipod may have to be mounted at /mnt/ipod, rather than /media/ipod.

Try linking the two locations (i.e. make /mnt/ipod point to /media/ipod).

If you're game you could also try the more advanced, but better, way of doing it that I've written up here: [https://wiki.ubuntu.com/KubuntuIpod](https://wiki.ubuntu.com/KubuntuIpod)

L.

EDIT: I just saw your last post.  I'm pretty sure that "vanilla" amarok needs the ipod at /mnt/ipod.  The version of amarok distributed by Kubuntu looks at /media/ipod (I think).  This is most likely your problem.  You could either move your ipod mount point to /mnt/ipod or reinstall Amarok from kubuntu repositories (see [http://kubuntu.org/announcements/amarok-1.3.7.php](http://kubuntu.org/announcements/amarok-1.3.7.php))

---

### Post by 23meg on 2005-12-11
Is it connected via USB? Is it mounted and accessible normally? What's your fstab line for the ipod?

---

### Post by PheonixRising on 2005-12-11
[QUOTE=ltmon]Your ipod may have to be mounted at /mnt/ipod, rather than /media/ipod.

Try linking the two locations (i.e. make /mnt/ipod point to /media/ipod).

If you're game you could also try the more advanced, but better, way of doing it that I've written up here: [https://wiki.ubuntu.com/KubuntuIpod](https://wiki.ubuntu.com/KubuntuIpod)

L.[/QUOTE]

How do I link the two locations?

[QUOTE=23meg]Is it connected via USB? Is it mounted and accessible normally? What's your fstab line for the ipod?[/QUOTE]

It's connected via USB, it shows up when I plug it in to the computer, and shows up as /media/ipod. What's a fstab line?

---

### Post by 23meg on 2005-12-11
It's the line in your /etc/fstab file that defines how your ipod is mounted. If you don't have one, try adding one using [this guide]("http://www.ubuntuforums.org/showthread.php?t=36632").

---

### Post by PheonixRising on 2005-12-11
There wasn't a line for the ipod, so I added this:
```
/dev/sda2 /media/ipod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0
```

And it's still not working...

---

### Post by ltmon on 2005-12-11
Udev/HAL automatically mounts your ipod according to a set of rules (configured by Ubuntu).  In our case it will automatically mount it at /media/ipod, but should detect an fstab entry and revert to using it if it's found.  I'm not sure why yours does not work.

Are you sure your ipod is /dev/sda2?  Type "dmesg | tail" when you plug in your ipod (type it in beforehand too, so you can easily see the changes) and you should be able to find the device name.  It should be /dev/sda<something> anyway.

Also have a look at my fstab line (available part way through the wiki entry I linked before) and see if it looks the same as yours.  I know my line works on a 4th gen ipod photo formatted for Windows.

To do it by linking:

sudo ln -sf /media/ipod /mnt/ipod

L.

---

### Post by wall0159 on 2005-12-22
Hi folks,

I'm in a similar position. I installed amaroK 1.4 (on Breezy) from the same place, because I wanted AAC support. Works great, but for iPod connection. (same message)

My ipod mounts, but not 'properly'. It only mounts if it's connected during the boot process. But then it mounts ok. Rhythmbox can see it's contents, but not amaroK.

I typed 
>>sudo ln -s /media/ipod /mnt/ipod 
so that it's mirrored there too..

I also tried some of the things suggested by ltmon, but baulked at recompiling  halbackend.cpp

AFAIK, I have all the necessary stuff installed.. that is:
amaroK 1.4 and ipodslave, right?

Any thoughts would be great! :-)

Cheers,
-Angus

---

