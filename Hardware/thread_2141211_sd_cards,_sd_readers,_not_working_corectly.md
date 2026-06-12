---
title: "sd cards, sd readers, not working corectly"
date: 2013-05-02
forum: Hardware
---

### Post by klein de usa on 2013-05-02
hi 
this isn't a new problem it started out with the usb to ide adapters and went down hill every since, i just got a bran new raspberry pi and tried using the dd command to install the img on an sd card, well it had errors, that was on xubuntu 12.04 so i moved to a ubuntu 10.04 computer i had and it read the sd card but when i tried to use the dd command on it from this machine it said input output errors. so i rebooted the computer and then it wouldn't read the drive, the drive would blink but it wouldn't open it or mount it so i did sudo blkid well there the drive was hummmm gparted wasn't seeing it either. so i'm thinking well so i go and fire up my old buddy ubuntu 8.04 bang it reads the drive and mounts it well except the ext4 partition but at least it seen it and was smart enough to say i can't deal with ext4 partition, so on this 8.04 machine i fire up gparted and reformat the sd card everything worked out fine i stuck it back in the xubuntu 12.04 machine and it read the drive fine right now i'm using the dd command to right the img to my sd card so far so well and if it doesn't work i guess i going to have to go to my win7 machine, now wont that be something having to go to windows 7 to copy a deban.img to sd card for a Linux learning project

---

