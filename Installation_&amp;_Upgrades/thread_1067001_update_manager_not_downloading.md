---
title: "update manager not downloading"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by wpsmithii on 2009-02-11
Working with Ubuntu 8.04 LTS, when I try to update, the update manager is not downloading anything. I just got online with wireless and I can go to any website but I changed the GUI update download to a few kilobites and it is not doing it. Thanks in advance. Bill Smith

---

### Post by Partyboi2 on 2009-02-11
Can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
sudo apt-get update
```

---

### Post by wpsmithii on 2009-02-12
When I open the terminal and type sudo apt-get update, I get sudo: unable to resolve host Home2 and it's not asking me for my password. Home2 is the computer I'm using for this message. The page load is very slow too. Thanks for responding Bill

---

### Post by Partyboi2 on 2009-02-12
Looks like there could be a small problem with your hosts file. Can you open a terminal again and post the output to[FONT=monospace]
[/FONT]```
cat /etc/hosts
```and
```
hostname
```

---

### Post by wpsmithii on 2009-02-12
when I type:
cat /etc/hosts at the terminal prompt I get
127.0.0.1 local host
127.0.1.1 Home2.00-21-91-16-01-2F

#The following lines are dersirable for IPv6 capable hosts
::1 ip6-local host ip6-loopback
FE00::0 ip6-local net
ff00::0 ip6-mcast prefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

when I type:
hostname
I get
Home2

---

### Post by wpsmithii on 2009-02-12
By the way I don't know how to edit a file. I'm going to bed, I'm in Colorado. Bill

---

### Post by Partyboi2 on 2009-02-13
Press Alt+F2 and in the box that opens type
```
gksu gedit /etc/hosts
```
then change 
```
127.0.0.1 local host
127.0.1.1 Home2.00-21-91-16-01-2F
```
to
```
127.0.0.1 local host
127.0.1.1 Home2
```
then save and exit gedit.
Then open a terminal and try
```
sudo apt-get update
```
again.

---

### Post by Share_The_Pain on 2009-02-13
zzz

---

### Post by wpsmithii on 2009-02-13
When I press ALT+F2 and type: gksu gedit /etc/hosts there are several options: run in terminal, run with file, and run. I tried all of them and got no response. I must be doing something wrong. Should I put sudo in front of the phrase or what? Thanks Bill

---

### Post by Kevbert on 2009-02-13
Go to Applications-Accessories-Terminal and try typing in there.
```
gksu
```
is the graphical equivalent of
```
sudo
```

---

### Post by wpsmithii on 2009-02-13
Ok, when I type gksu at the terminal prompt I get a run box as root with a selection of (I'm assuming) user types. Then when I type gedit /etc/hosts in the run window I get a blinking cursor and nothing else. Same with typing gksu gedit /etc/hosts in the run box window. Sorry to be so much trouble. Bill

---

### Post by Partyboi2 on 2009-02-14
> Sorry to be so much trouble. Bill      It's no trouble :) 
Can you boot into recovery mode and try making the changes to your /etc/hosts file.
When you boot choose the recovery mode and login. Then type
```
nano /etc/hosts
```and make the changes as posted before. Then to save press Ctrl+o then "enter" Then to exit nano press Ctrl+x. Then reboot  by typing
```
reboot
```

---

### Post by wpsmithii on 2009-02-14
Fianlly that did it. Thanks so much for your patience and assistance. I learned alot. I hope that new fire is not close to you. Thanks again. Bill Smith The thread tools menu does not have the option to mark the thread as solved.

---

### Post by Partyboi2 on 2009-02-14
> Fianlly that did it. Thanks so much for your patience and assistance. I learned alot. I hope that new fire is not close to you. Thanks again. Bill Smith The thread tools menu does not have the option to mark the thread as solved.
Happy to help :)
There were recent problems with the forum database so they have temporarily disabled the option to mark a thread solved. Hopefully it will return soon.

---

