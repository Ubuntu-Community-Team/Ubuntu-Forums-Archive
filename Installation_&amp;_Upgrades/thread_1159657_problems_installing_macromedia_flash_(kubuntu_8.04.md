---
title: "problems installing macromedia flash (kubuntu 8.04)"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by marahl on 2009-05-14
Hello I just received out new PC with Kubuntu 7 pre installed we upgraded to 8.04.  This is my first experience with linux and I have been having lots of issues viewing google street view and any form of videos because I apparentely don't have adobe flash.  I have gone through many steps, read many forums and most command lines don't work for some reason. This is some of what I have tried in my terminal. 

user@usercomputer:~$ sudo dpkg -i install_flash_player_10_linux.deb
[sudo] password for user:
dpkg: error processing install_flash_player_10_linux.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 install_flash_player_10_linux.deb
user@usercomputer:~$ sudo apt-get install linuxdcpp
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linuxdcpp
user@usercomputer:~$

any suggestions at this point would help
Thanks

---

### Post by theozzlives on 2009-05-14
> **marahl said:**
> Hello I just received out new PC with Kubuntu 7 pre installed we upgraded to 8.04.  This is my first experience with linux and I have been having lots of issues viewing google street view and any form of videos because I apparentely don't have adobe flash.  I have gone through many steps, read many forums and most command lines don't work for some reason. This is some of what I have tried in my terminal. 

user@usercomputer:~$ sudo dpkg -i install_flash_player_10_linux.deb
[sudo] password for user:
dpkg: error processing install_flash_player_10_linux.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 install_flash_player_10_linux.deb
user@usercomputer:~$ sudo apt-get install linuxdcpp
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linuxdcpp
user@usercomputer:~$

any suggestions at this point would help
Thanks

If you have the deb file:
```
sudo dpkg -i *nameofdebfile*.deb
```

---

### Post by spcwingo on 2009-05-14
You could also use this one command to pull in flash, java, and a whole lot more:

```
sudo apt-get install ubuntu-restricted-extras
```

EDIT:  I just noticed that you're on Kubuntu, so that command would be:

```
sudo apt-get install kubuntu-restricted-extras
```

---

### Post by marahl on 2009-05-15
Thanks for the fast replies but unfortunately neither of the suggestions worked. The first suggested command line resulted in the following:

user@usercomputer:~$ sudo dpkg -i install_flash_player_10_linux.deb
[sudo] password for user:
dpkg: error processing install_flash_player_10_linux.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 install_flash_player_10_linux.deb

The command line provided by Spc resulted in the following:

user@usercomputer:~$ sudo apt-get install kubuntu-restricted-extras
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package kubuntu-restricted-extras



We have been getting the "couldnt find package" message with just about everything we have tried...... Any more suggestions?    Thank You

---

### Post by spcwingo on 2009-05-15
Have you enabled universe and multiverse repos in synaptic?  That may be the reason for the "couldn't find package" error.

---

