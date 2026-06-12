---
title: "Getting back my wifi"
date: 2010-07-08
forum: Hardware
---

### Post by braiamp on 2010-07-08
I'm opening this thread following the topic forum organization. The original thread are on [http://ubuntuforums.org/showthread.php?p=9557636](http://ubuntuforums.org/showthread.php?p=9557636).

As above described, I changed all my system root to bind user and getting back to root. But a consecuent of that are vary and maybe take some time to get resolved, but the topic of the thread is:

I use the root user to get a X session (i kwon, bad idea) on my system, nm-applet doesn't start on my default user by in the root do, but when i try to manage my wifi conections i only see: The device is not ready or something like this. I already make modprobe, and iwconf read the device but it lost in the track to allow NetworkManager  manager the device.

---

### Post by braiamp on 2010-07-08
> **braiamp said:**
> I'm opening this thread following the topic forum organization. The original thread are on [http://ubuntuforums.org/showthread.php?p=9557636](http://ubuntuforums.org/showthread.php?p=9557636).

As above described, I changed all my system root to bind user and getting back to root. But a consecuent of that are vary and maybe take some time to get resolved, but the topic of the thread is:

I use the root user to get a X session (i kwon, bad idea) on my system, nm-applet doesn't start on my default user by in the root do, but when i try to manage my wifi conections i only see: The device is not ready or something like this. I already make modprobe, and iwconf read the device but it lost in the track to allow NetworkManager  manager the device.
Note: I have access to the whole system but not runnig on it. Who's want to tell me that post some log I have the access

---

### Post by jalirious on 2010-07-08
wicd is a very effective, intuitive alternative to network manager - I suggest giving it a whirl.

---

### Post by braiamp on 2010-07-08
> **jalirious said:**
> wicd is a very effective, intuitive alternative to network manager - I suggest giving it a whirl.
I allready used it, on another pc. The only problem is that I can't do sudo anything, and if i download it, i cannot get that the driver get mount, as I post on [http://ubuntuforums.org/showthread.php?p=9563113#post9563113](http://ubuntuforums.org/showthread.php?p=9563113#post9563113), but whatever thanks.

---

### Post by braiamp on 2010-07-08
> **braiamp said:**
> I allready used it, on another pc. The only problem is that I can't do sudo anything, and if i download it, i cannot get that the driver get mount, as I post on [http://ubuntuforums.org/showthread.php?p=9563113#post9563113](http://ubuntuforums.org/showthread.php?p=9563113#post9563113), but whatever thanks.
The main problem is that my primary (unique) access to the internet (wifi) doesn't work. And if it work, the problem with su - sudo could be resolved with aptitude reinstall all package.

---

### Post by braiamp on 2010-07-11
Well, I maybe have to change the way that want the answer that I´m  looking for make my system work as expected.
Some of the device files, configuration files, binary link, library or  anyelse that should be in a exact uid, user or group owned? I attach the  last list of the package that I have installed to build my entire  system with apt-build but didn't do for time and energy reasons, on my  HP Pavilion a1104x, I use a realtech firmware on a Encore build pci card.

Here is how my system have set the users and groups:
/dev/* = root
/etc/* = root, included NetworkManager folder
/*bin = root
/usr/*bin = root
/usr/* = root
/home/* = his respective users and /home by root
/var/log = the syslog user and the user especific for each log file
/var/* = root
/lib/udev = root, maybe it would have another user but yet I don't know
/lib/security = root
/lib/* = root
/* = root
everyelse don't listed = root

Any help would be apreciated.

---

### Post by braiamp on 2010-07-11
I forget it, the attachment.

---

### Post by braiamp on 2010-07-11
Following the steps that I take in [http://ubuntuforums.org/newreply.php?do=postreply&t=1526611](http://ubuntuforums.org/newreply.php?do=postreply&t=1526611), the device start to work again. The command that i run

```

root@braiam-desktop:~# dpkg-reconfigure udisks dbus
Ya existe el usuario del sistema `messagebus'. Saliendo.
start: Job is already running: dbus
root@braiam-desktop:~# 

```

---

