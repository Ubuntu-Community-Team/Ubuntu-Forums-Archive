---
title: "Dell inspiron 6400 issue no brightness control"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by ishmeetahuja on 2007-02-11
Hi,

 I am newbie to Linux world. I have recently installed Kubuntu on my Dell Inspiron 6400. 
I also installed Beryl and had no problems with the installation.

Only thing which I am not able to do is the brightness control using special Function Keys.

Generally Fn + Up arrow or down arrow is used to increase/decrease brightness level. I am unable to do so in kubuntu.

Please help and advise....

---

### Post by jimbo111 on 2007-02-12
I'm having the same problem with my HP compaq nc6000 laptop. Fn up and down to control brightness doesn't work with my Ubuntu Edgy Eft 6.10. I just posted a thread but I guess I should  have searched first for this topic. Apparently, brightness is suppose to be controlled in the Power Management feature, but no brightness controls can be found there as per Ubuntu Help. I'm wondering as well if anyone knows how to do this too........ :confused:

---

### Post by ishmeetahuja on 2007-02-12
hey i figured that out with the help of some extensive findings on the internet.

Atleast it started working on my system

[https://bugs.launchpad.net/distros/u....17/+bug/74284](https://bugs.launchpad.net/distros/u....17/+bug/74284) gives a way to solve this issue.

1. open and edit the file /etc/modprobe.d/blacklist

2. Append "blacklist video" at the end of the file.

3.Reboot

I was able to regain brightness control on my Dell Inspiron 6400.

Try it out and wish u a good luck.

---

### Post by dirkb on 2007-02-12
link doesnt work

---

### Post by ishmeetahuja on 2007-02-12
Hey I am sorry

But the workaround works pretty well


Try it out...

---

### Post by Tulsapoke on 2007-02-17
This fix worked for our 6400 with the ATI 3D card.  This worked out of the box on my identical 1500 with the Intel card.  Thanks for posting this!

---

### Post by nachotronics on 2007-02-18
It worked for me also, thanks a lot! \\:D/

---

### Post by ishmeetahuja on 2007-02-23
No problem guys!!!!

njoy!!

---

### Post by kennygunie on 2007-03-03
Thank you. It works nice :)

---

### Post by sloter on 2007-03-31
Hello,

ishmeetahuja, the modification of /etc/modprobe.d/blacklist works fine on my inspiron 6400, thank you!

a link launchpad [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/74284]("https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/74284")

have fun!
SR

---

### Post by LarryJ2 on 2007-12-17
On my Dell Inspirion E1505,  I installed  gnome-power-manager on my KDE/Kubuntu 7.10 installation.   Now when I press Fn+ UpCursorKey  or Fn+DowncursorKey,  I get a LCD backpanel brightness window which briefly appears and I am able to control the LCD brightness without modifying  /etc/modprobe.d/blacklist.

LJ

---

