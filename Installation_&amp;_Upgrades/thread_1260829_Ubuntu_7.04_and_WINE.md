---
title: "Ubuntu 7.04 and WINE"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by mr.karevski on 2009-09-08
Hello guys! Im new here so i dont know where to put my question, if this topic not belong here please send it do other category. Im new at linux, i dont know very much about it, i have installed an Ubuntu 7.04 on my old pc, (I dont have a pc for the newest versions). I want to install Wine on this ubuntu, i have tried with synaptic and doesnt work.. i have tried some of the packages and doest want to install, i tried with some codes on Terminal also doesnt work.. Can somebody please help me about this, with step by step operation. i need this to run WinBox.. please help.. greetings from macedonia, and sorry about my english..:) Cheers!

---

### Post by Partyboi2 on 2009-09-08
Hi, 7.04 has reached its end of life that is why you have not been able to install wine through the terminal or using synatpic. If you are able to it would be better to upgrade to a later release.
If you cannot upgrade or want to stay with Feisty then you will need to make some changes to your /etc/apt/sources.list file.
Open a terminal (Applications>Accessories>Terminal) and open your sources.list
```
gksu gedit /etc/apt/sources.list
``` Then put a # in front of all the lines starting with 'deb' then at the bottom of the file add
```
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
```
do not put a # in front of those ones though.
Once done save the changes and close gedit, then back in the terminal
```
sudo apt-get update
sudo apt-get install wine
```

---

