---
title: "My Ubuntu update~!"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by kyqinqiqin on 2009-05-22
[SIZE=5][FONT=Arial]I want to made my Ubuntu update,but this have something wrong in it. I don't know how to fix it. I put on two pictures in here. Thanks in all answer.~!:)[/FONT][/SIZE][IMG]http://ubuntuforums.org/picture.php?albumid=1125&pictureid=4011[/IMG]
[IMG]http://ubuntuforums.org/picture.php?albumid=1125&pictureid=4012[/IMG]

---

### Post by theOtherMarino on 2009-05-22
Your error may occure because your /boot is full.

Post here the result of df -h 

In the list you should see your /boot directory. If it's nearly full (90% or more), then you have no more room to store your update.

Drop to a terminal, change directory to /boot and list the files with ls -l
Post the result here.

Marino

---

### Post by kyqinqiqin on 2009-05-23
[SIZE=5][FONT=Trebuchet MS]I checked my /boot.But there is not full. Please look at the picture. I don't know there is tell me what a information.[IMG]http://ubuntuforums.org/picture.php?albumid=1125&pictureid=4013[/IMG]

I arrived a many of bbs of ubuntu. They said I could like to del something and update on it. 

Example:
sudo rm -fv /boot/initrd.img-2.6.27.bak
sudo rm -fv /boot/vmlinuz-2.6.27-generic
sudo rm -fv /boot/config-2.6.27-7-generic
sudo rm -fv /boot/abi-2.6.27-7-generic
sudo rm -fv /boot/system.map-2.6.27-7-generic
sudo apt-get update
sudo apt-get upgrade

Do you agree it. This's meansure.
[/FONT][/SIZE]

---

