---
title: "HVR-2200 Install help please...."
date: 2021-04-14
forum: Hardware
---

### Post by leejenon on 2021-04-14
Hi

Could I have some help please with installing my Haupauge HVR-2200 TV PCIe card...

I have been following the instructions here but I only get this far...

[https://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200](https://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200)

```
lee@Plex-TV:/$ sudo apt-get install get patchutils lsdiff libproc-processtable-perl build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package get
E: Unable to locate package lsdiff
lee@Plex-TV:/$ 
```

It doesn't seem to put an error in the syslog

```
Apr 14 15:04:44 Plex-TV dbus-daemon[735]: [session uid=1000 pid=735] Successfully activated service 'org.gnome.gedit'
Apr 14 15:05:15 Plex-TV PackageKit: daemon quit
Apr 14 15:05:15 Plex-TV systemd[1]: packagekit.service: Succeeded.

```

Thanks

Lee (Linux newbee)

Ubunto 20..04.20

---

### Post by CelticWarrior on 2021-04-14
A device from 2009 that by now still isn't supported it will never be.
Old code won't work with newer kernels.

Try opening Additional drivers. If there are drivers/firmware for that old card available they can be selected and applied there. If there's nothing proposed your card is as good as dead at least in what concerns Linux. It may or may not have native support in the current Windows versions (8/10) but if not its old drivers won't work either.

---

### Post by deadflowr on 2021-04-14
lsdiff is already in patchutils.
I wonder if  get means git, as the very next command to run is a git command, and none of the other listed packages are git.

---

### Post by leejenon on 2021-04-16
Thanks for your replies.

I think I better get a new card!

Lee

---

