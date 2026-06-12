---
title: "Asus B43S-X51 and 3D"
date: 2012-05-08
forum: Hardware
---

### Post by rotten777 on 2012-05-08
I've read [this thread]("http://ubuntuforums.org/showthread.php?t=1930450"), and it doesn't work getting the ATI card rendering in 3D. 

As I first installed 12.04, it was rendering in 3D. I think it was when I tried to install the restricted drivers when it first goofed up the Intel card's 3D. Is there anything short of a reinstallation that can be done to get the 3D back?

---

### Post by rotten777 on 2012-05-23
To anyone that runs across this, I've ended up getting 3D to work. I don't believe it is the ATI card doing it though. If you just want your B43S-X51 to work in Unity 3D, do this:

```
sudo apt-get purge nvidia*
sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64
sudo dpkg-reconfigure xserver-xorg
sudo reboot
```

---

### Post by goaliedude3919 on 2012-05-23
I don't know what kind of CPU you have, but if you have an intel CPU, odds are it has an Optimus  GPU built in and this can be causing problems by forcing the system into Unity2D as opposed to Unity3D. Enter this line into a Terminal to find out if this is happening:
```
echo $DESKTOP_SESSION
```
If it says Unity2D, then something is preventing you from booting in Unity3D. To disable Optimus, reboot your computer and enter the BIOS. There should be an option there for Optimus where you can disable it. That should hopefully give control to the actual GPU which will be capable of running Unity3D.

---

