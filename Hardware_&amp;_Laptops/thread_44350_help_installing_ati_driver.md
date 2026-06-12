---
title: "help installing ati driver"
date: 2005-06-25
forum: Hardware &amp; Laptops
---

### Post by DarkManX4lf on 2005-06-25
when i run glxgears i only get around 150fps (i have a ati radeon 9800) and i assume its because my ati drivers are not installed properly....so when i try to follow this guide:

[http://www.ubuntuforums.org/showthread.php?t=24557&highlight=AT](http://www.ubuntuforums.org/showthread.php?t=24557&highlight=AT)

i dont know  my kernel version how would i get my kernel version ?

---

### Post by DarkManX4lf on 2005-06-25
ok so i followed this guide instead

[http://www.ubuntuforums.org/showthread.php?t=32495&highlight=ati+driver](http://www.ubuntuforums.org/showthread.php?t=32495&highlight=ati+driver)

and now after the installation, i typed this like the guide says


# sudo gedit /etc/X11/xorg.conf 


and when i did it opened the xorg.conf file and there was NOTHING in the file, it was blank.............


what did i do wrong?  i am doing this froma  fresh install of ubuntu....can someone aid me here ? :)


btw: i am using the 64bit version of ubuntu

---

### Post by DarkManX4lf on 2005-06-25
ummm also to add


when i go into the terminal and type

startx

this is what it says


```


X: warning; process set to priority -1 instead of requested priority 0

X Window System Version 6.8.2 (Ubuntu (static) 6.8.2-10 20050405154247 root@)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 x86_64 [ELF]
Current Operating System: Linux ubuntu 2.6.10-5-amd64-generic #1 Tue Apr 5 12:21:57 UTC 2005 x86_64
Build Date: 05 April 2005
        Before reporting problems, check http://wiki.X.Org
        to make sure that you have the latest version.
OS Kernel: Linux version 2.6.10-5-amd64-generic (buildd@king) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:21:57 UTC 2005
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun 25 20:13:48 2005
(==) Using config file: "/etc/X11/xorg.conf"
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
Could not init font path element unix/:7100, removing from list!

waiting for X server to shut down


```

also WHENEVER i type startx and after it doenst open or work or w/e i cant open any other programs........like if i tired to open gaim, mozilla, even if i tried to go into file browser it just shows in the taskbar that its starting what ever and it never starts...i would have to log out and then login

any suggestions?

---

### Post by DarkManX4lf on 2005-06-25
ok i have pretty much no clue what im doing, i am a linux newb, the only thing i know to do with/in linux is to install it and point and click.....

so i reinstalled ubuntu, now can someone guide me on how to install the latest stable ATI drivers for linux? from there i want to run cedega and see if i can get some windows games to run....

so anyone?

---

### Post by dezgot on 2005-06-26
have you tried the really old ones available through Symantec?  I followed a guide for the new ones and of course it didn't work, so i used the packaged install and now i get the proper fps in glxgears for my card.  Maybe a newer Symantec package will be released soon for the newer drivers...

---

