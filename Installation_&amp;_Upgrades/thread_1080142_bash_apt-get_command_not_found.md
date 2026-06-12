---
title: "bash: apt-get: command not found"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by arijitm on 2009-02-25
guyzzzzzzzzzzzzzzz save meeeeeeee!!!!!!!!!!!! ](*,) ](*,)
my apt-get is not working, i am doomed.... i have three project enviorments installed and if i have to re-install my os i ll die......

OS :: Kubuntu
Machine :: lenovo
Problem :: i used - sudo apt-get install git-core - 
                  - bash: apt-get: command not found - :(
           used   - sudo apt-cache search git | grep "git" -
                  - bash: apt-get: command not found -
           plzzzzzz save me.........

---

### Post by sisco311 on 2009-02-25
is /usr/bin in your $PATH?
```
echo $PATH
```

what's the output of:
```
type apt-get
```
and
```
ls -al /usr/bin/apt-get
```

try ```
/usr/bin/apt-get update
```

---

### Post by arijitm on 2009-02-25
[COLOR="Blue"]**typed :**[/COLOR] echo $PATH
[COLOR="Blue"]**output :**[/COLOR] /home/arijitm/java/jdk1.5.0_11/bin:/home/arijitm/java/maven-2.0.6/bin:/home/arijitm/myJava/apache-ant-1.7.1/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

------------------------------------
[COLOR="Blue"]**typed :**[/COLOR] apt-get
[COLOR="Blue"]**output :**[/COLOR] bash: apt-get: command not found

------------------------------------
[COLOR="Blue"]**typed :**[/COLOR] ls -al /usr/bin/apt-get
[COLOR="Blue"]**output :**[/COLOR] ls: /usr/bin/apt-get: No such file or director

------------------------------------
[COLOR="Blue"]**typed :**[/COLOR] /usr/bin/apt-get update
[COLOR="Blue"]**output :**[/COLOR] bash: /usr/bin/apt-get: No such file or directory

---

### Post by sisco311 on 2009-02-25
try to reinstall apt.

you can download it from: [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

### Post by arijitm on 2009-02-25
There is a list of packages what to install ?? m clueless !!!!!!
    * dapper (6.06LTS)
    * dapper-updates
    * dapper-backports
    * gutsy (7.10)
    * gutsy-updates
    * gutsy-backports
    * hardy (8.04LTS)
    * hardy-updates
    * hardy-backports
    * intrepid (8.10)
    * intrepid-updates
    * intrepid-backports
    * jaunty
-----  sorry for my stupid or illiterate questions  -----

---

### Post by sisco311 on 2009-02-25
Search for "apt" and select the ubuntu version you are running.


or post the output of:
```
uname -a
```
and
```
cat /etc/issue
```

---

### Post by arijitm on 2009-02-25
for : uname -a
came : Linux arijitm-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

----------------------
for : cat /etc/issue
came : Ubuntu 7.10 \n \l

---------------------------

searched with "apt" had many results.... bt none for "apt-get"

---

### Post by Partyboi2 on 2009-02-25
Try [[COLOR=Blue]this[/COLOR]]("http://packages.ubuntu.com/gutsy/apt") page, down the bottom  choose i386 to download.

---

### Post by arijitm on 2009-02-25
i did exactly that buddy, but this is what it came out....

---------------------------------------------
[COLOR="Red"]$ sudo dpkg -i /home/arijitm/Desktop/apt_0.7.6ubuntu14_i386.deb
Selecting previously deselected package apt.
dpkg: regarding .../apt_0.7.6ubuntu14_i386.deb containing apt:
 dpkg conflicts with apt (<< 0.7.7)
  apt (version 0.7.6ubuntu14) is to be installed.
dpkg: error processing /home/arijitm/Desktop/apt_0.7.6ubuntu14_i386.deb (--install):
 conflicting packages - not installing apt
Errors were encountered while processing:
 /home/arijitm/Desktop/apt_0.7.6ubuntu14_i386.deb[/COLOR]
----------------------------------------------

---

