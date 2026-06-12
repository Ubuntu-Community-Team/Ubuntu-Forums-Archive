---
title: "multi installs, messy grub, need cleaning help."
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by kiwimenace on 2009-07-09
HI guys, another new linux and specificly ubuntu user. Finally, after many years of knowing that i should have, I have changed to linux. Just over a week ago and loving it, only thing i need now is to get my QIII sorted and ill have no need at all for windows. All in all its been quite an exciting challenge and actually a bit easier than expected, very happy, its a move that will certainly not be reversed!

But i need some help from some of you knowledgeable guys to get my system cleaned up a bit. Initially i started with a single partition of "vista" then i threw in the ubuntu 9.04 cd and from that created a dual boot system. All good. Then i thought id like to see what kubuntu was like so i burnt up a disk of that and proceeded down the same path and now I've got a triple boot system. All good, works fine except there is double entries of everything in grub and I would like to know how to choose what the grub will auto load if left untouched on start up.

So i would like to get two things done A, get rid of the kubuntu install, i see all the partiotions from inside the windows install and could no doubt just delete partiotions and it would be gone but I dont know what partition to delete and also I don't want to delete the grub partition and loose boot of ubuntu and B, when ive got that sorted id like to sort my grub up and get rid of my double entries and choose default boot.

Any help will be greatly appreciated.

P.S. i also know now that this was not the correct way to try Kubuntu. lol

---

### Post by zvacet on 2009-07-09
If you made one partition for every install then Kubuntu should be on your sda3,because sda1 is Windows sda2 Ubuntu.You can download [Gparted live CD]("http://gparted.sourceforge.net/") and delete partition,and then extend Ubuntu partition on free space or you can make separate home partition.If yopu want to try Kubuntu you can follow [this.]("http://psychocats.s465.sureserver.com/ubuntu/kde") Yous in case type in terminal 

```
fdisk -l
```

and post output here.

---

