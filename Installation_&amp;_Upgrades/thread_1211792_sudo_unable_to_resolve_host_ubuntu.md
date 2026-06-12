---
title: "sudo: unable to resolve host ubuntu"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by healee on 2009-07-13
Coincidentally I call my ubuntu system "ubuntu".  Every time I do a sudo I get the message "sudo: unable to resolve host ubuntu" even though it has no problem executing the command.  What does this mean?  Why does it do what it does?

---

### Post by JohnnySage50307 on 2009-07-13
I'm not entirely certain, but it is possible that "ubuntu" is a restricted hostname, much like how "root" is restricted.  My advice is to change your hostname to something like ABC-Ubuntu, where "ABC" can be your initials.

---

### Post by healee on 2009-07-13
> **JohnnySage50307 said:**
> I'm not entirely certain, but it is possible that "ubuntu" is a restricted hostname, much like how "root" is restricted.  My advice is to change your hostname to something like ABC-Ubuntu, where "ABC" can be your initials.
Thanks!  Where do we change the hostname???

---

### Post by wojox on 2009-07-13
gksu gedit /etc/hostname

---

### Post by doas777 on 2009-07-13
hit Alt + F2 and enter 
gksu gedit /etc/hosts

here is mine:
```

127.0.0.1    localhost
127.0.1.1    21of2

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```make sure that there is a line like:
```
127.0.0.1    ubuntu
```if it is followed with '.local' or .domain.com or whatever, then sudo will not work. change it back to look like the line above, save and exit gedit. then you shoudl be able to sudo.

gutsy and hardy used to append my fully qualified domain name every time I opened and closed the network manager. ultimatly i added 21of2.domainname.net to the end of the localhost line so it would stop.

good luck

---

### Post by healee on 2009-07-13
> **wojox said:**
> gksu gedit /etc/hostname
Thank you!  When do we use "gksu" instead of "sudo".  It doesn't even ask me to enter password.

---

### Post by healee on 2009-07-13
> **doas777 said:**
> hit Alt + F2 and enter 
gksu gedit /etc/hosts

here is mine:
```

127.0.0.1    localhost
127.0.1.1    21of2

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```make sure that there is a line like:
```
127.0.0.1    ubuntu
```if it is followed with '.local' or .domain.com or whatever, then sudo will not work. change it back to look like the line above, save and exit gedit. then you shoudl be able to sudo.

gutsy and hardy used to append my fully qualified domain name every time I opened and closed the network manager. ultimatly i added 21of2.domainname.net to the end of the localhost line so it would stop.

good luck
Thank you!  Having got the hostname set in the host file, the error message does not come up any more.  I wonder why every "sudo" needs to resolve the hostname.

---

### Post by doas777 on 2009-07-14
> **healee said:**
> Thank you!  When do we use "gksu" instead of "sudo".  It doesn't even ask me to enter password.

gksu is for graphical applications, whereas sudo is for command line apps. gksu usually asks for a password, but both sudo and gksu share a timer, and if a subsequent sudo is used before the timer expires, then the access is granted (since you just gave it your passwd a min ago.)

have fun

---

### Post by healee on 2009-07-14
> **doas777 said:**
> gksu is for graphical applications, whereas sudo is for command line apps. gksu usually asks for a password, but both sudo and gksu share a timer, and if a subsequent sudo is used before the timer expires, then the access is granted (since you just gave it your passwd a min ago.)

have fun
Thank you for your great help!

---

### Post by healee on 2009-07-16
When I tried the same on my laptop with ubuntu 9.04 installed I got the following errors.  Please help!

healee@ubuntu-laptop:~$ gksu gedit /etc/hostname
No protocol specified
(gedit:3904): Gtk-WARNING **: cannot open display: :0.0
healee@ubuntu-laptop:~$ gksu gedit /etc/hosts
No protocol specified
(gedit:3906): Gtk-WARNING **: cannot open display: :0.0

---

