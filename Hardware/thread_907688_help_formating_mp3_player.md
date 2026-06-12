---
title: "help formating mp3 player"
date: 2008-09-01
forum: Hardware
---

### Post by xd397 on 2008-09-01
Hi I have a mp3 player that is read as a flash drive an I have an error when I start the player that says (unknown format please reformat). The only problem is that linux and windows wont open the drive. any advice is welcome

---

### Post by aysiu on 2008-09-02
Can you plug the MP3 player in, paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal), and then post the output back here? ```
sudo fdisk -l
df -h
dpkg -s gparted
cat /etc/apt/sources.list
```

---

