---
title: "Dual Boot/Error 15/How to Uninstall???"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by WackyCat on 2008-12-11
Hello: I am having the following problem: For several months, I have been experimenting with Ubuntu, and I had it dual booting with XP. I have to uninstall Ubuntu, but cannot figure out how to do it without reformatting the drive and losing all of my XP programs. I tried booting with the XP CD, using Recovery Console and the FIXMBR and FIXBOOT commands, but this did not seem to do anything...except now when the dual boot menu comes up and I select Ubuntu, I get Error 15. Any help would be appreciated (please note that I am a complete newbie as far as Ubuntu goes).

Thanks, Steve

---

### Post by Partyboi2 on 2008-12-11
To uninstall ubuntu you can boot a ubuntu live cd and go to gparted (System>Admin>Partition Editor) and delete your ubuntu installation. Then you would boot the xp disk to recovery and use the fixmbr command.

---

### Post by caljohnsmith on 2008-12-11
Do you have more than one HDD? Or do you have Ubuntu installed inside of Windows (Wubi install)? In other words, in Windows do you have a C:\ubuntu directory? How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. That will help clarify your setup.

---

### Post by WackyCat on 2008-12-11
Partyboi2 and caljohnsmith: Thanks for the quick replies. Well, I want to try your suggestions, but now I have another problem..I now constantly have a "Error reading boot CD...Reboot" message come up after choosing a language and then trying one of the selections. I thought maybe it was a bad burn...so I downloaded another copy of the ISO file (8.04.1), but the same thing happens. I do not have any problems reading other cd's. Any suggestions??

Steve

---

### Post by caljohnsmith on 2008-12-11
Did you check the MD5 sum of the Ubuntu ISO you downloaded? If you need an MD5 sum program in Windows, you could try:

[http://www.nirsoft.net/utils/hash_my_files.html](http://www.nirsoft.net/utils/hash_my_files.html)

Also, did you try burning the CD at 4X or slower? Can you use other CDs burned in your CD drive OK? You might try burning the Ubuntu CD using another computer's CD drive.

---

### Post by WackyCat on 2008-12-11
The MD5 on the downloaded ISO is good..I am going to try to make another burn at a slower speed as recommended. I will post back when I know if it works. Thanks caljohnsmith

---

### Post by WackyCat on 2008-12-11
Well, I burned two disks on two different burners, and tried them on two different computers...still the same error. Getting late, so I am going to sleep on this. Thanks for the suggestions so far.

Steve

---

