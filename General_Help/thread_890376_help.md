---
title: "help"
date: 2008-08-15
forum: General Help
---

### Post by katabarwa on 2008-08-15
i just ordered the disk from ubuntu and i was wondering if any body wants to walk me threw **[SIZE="2"]ALL[/SIZE]** the steps because when i tried it couldn't work please and thank you. p.s I'm from Canada,Saskatchewan

---

### Post by Uchiha_madara on 2008-08-15
> **katabarwa said:**
> i just ordered the disk from ubuntu and i was wondering if any body wants to walk me threw **[SIZE="2"]ALL[/SIZE]** the steps because when i tried it couldn't work please and thank you. p.s I'm from Canada,Saskatchewan



Excuse me ....... I understand from you that you tried to install
ubuntu but there is no result, aren't you ??

or Explain the Question again to me ??

---

### Post by Mashy on 2008-08-15
Basically, you put the disk into your disk drive, reboot your computer (making sure that the bios will boot from a disk before your hard drive. To do that, during start up it will say something like "Press f8 to enter setup", it varies from computer to computer. Then go to something like 'advanced bios settings', and there should be two or three options saying something like "boot 1" etc. Then you press enter on one of these, and set the first one to cd drive, second one to hdd-1, then exit and save your changes. It should be something like that, like I said, it varies. If you aren't sure, don't do anything, and get somebody who knows what to do to do it for you).

Then, the menu should load up. If you want to try ubuntu before installing it, select that option. If not, click on install. Then you need to input various information, such as what keyboard layout you use, and where you are in the world. 
Then it will load up the partition manager. You can either let it install to your hard drive, overwriting everything that is on there, or you can set up a partition, keeping your original files safe. 
I don't know too much about setting up partitions, as I got a friend to help me, but if you google search then you should find something.

Good luck!

---

### Post by BarryMaccaukner on 2008-08-15
1)Insert the disk
2)Go into boot menu by pressing f1 or f2 or f12 or delete it varies on computers
3)Select boot from cd
4)Restart with the cd in
5)Select start or install Ubuntu
6)Play around on the live cd and see how well it works for you
7)Click on the install icon
8)Select keyboard layout , language, and time zone
9)Partition: either let ubuntu walk you through and use the whole drive or do it yourself. You will need at least 2 partitions.
Your primary partition; this will be labeled as /  which is the root.
This partition should be formatted as ext3 or reiserfs , I recommend ext3
You will also need a linux swap partition. This can be small 500mb -1gb and
should be formatted as linux swap.
If you want you can make another partition /home for data
then when you install another linux os you can do so without upsetting your data.
10) Create a username and password
11) restart
Good luck

---

