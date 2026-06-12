---
title: "rpm packages"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by sdb2028 on 2006-02-18
How do you install rpm packages?

How do you do it from root?

How can you get a root desktop?
:confused: :confused:

---

### Post by kaamos on 2006-02-18
Hello!

1 & 2) alien can do this
```
sudo apt-get install alien
sudo alien -i name_of_package.rpm
```

3) don't do it, its not secure, sensible or fun. :neutral:
Just use sudo. [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by codejunkie on 2006-02-18
[QUOTE=sdb2028]How do you install rpm packages?

How do you do it from root?

How can you get a root desktop?
:confused: :confused:[/QUOTE]
question 1
```
sudo apt-get install alien
```
then 
```
sudo alien nameofpackage.rpm
```
question 2
you add the "sudo" or the "gksudo" perfix in front of a command
if you launch a command as root by pressing Alt+F2 you must use the "gksudo" prefix.
question 3
press Ctrl+Alt+F1 enter ```
sudo /etc/init.d/gdm stop
```switch to root with ```
sudo su
```and type```
startx
```
or do it the easy way by entering "sudo" in front of the app you need root access with for example to browse the file system as root press Alt+F2 and enter
```
gksudo nautilus
```

---

### Post by sdb2028 on 2006-02-18
Thanks, I got the RPM part configured and sudo works from terminal.

How do you get to a root in the graphical file browser? I am trying to install the new version of Firefox, and it tells me I don't have permission.

---

### Post by Ghetto_Smurf on 2006-02-18
yes, do it with debian. case you don't have any linux experience, DONT activate root. root is disabled for security reasons, yes, it can be activated but only if you know what you are doing. got lots of friends who need it for server reasons, but if you don't need for something special, dont do it. to install sutff, you got su. better that way

---

### Post by sdb2028 on 2006-02-18
There are things I need to do in root. I am fairly new to Linux, and new to ubuntu but am not unskilled at operating systems. I could probably figure it out if given enough time, however if someone else is willing to part with the knowledge I am willing and desire to learn all I can about this system.
So, how do you log in to root when starting ubuntu initialy?

---

### Post by Lord Illidan on 2006-02-18
[quote=sdb2028]There are things I need to do in root. I am fairly new to Linux, and new to ubuntu but am not unskilled at operating systems. I could probably figure it out if given enough time, however if someone else is willing to part with the knowledge I am willing and desire to learn all I can about this system.
So, how do you log in to root when starting ubuntu initialy?[/quote]

Not using root is the best solution. You are trying to install firefox. Are you doing it as per [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) ? If so, where does it give you an error?

---

### Post by Ghetto_Smurf on 2006-02-18
as you say, you are new to linux. DONT ACTIVATE THAT ROOT. use su, for cristsakes. well, if you want that root that much, do:

> su passwd root

after that, go for the gdm settings and allow administration to log in. otherwise you will only log in to root by text mode.

---

