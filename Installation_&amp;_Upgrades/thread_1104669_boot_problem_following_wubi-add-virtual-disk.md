---
title: "boot problem following wubi-add-virtual-disk"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by gazD on 2009-03-23
Hi,
I recently set up Ubuntu 8.10 via Wubi on my Lenovo Thinkpad T61p, which is also running windows Vista. Everything was working well for a few days, until today I decided that I needed more disk space for Ubuntu.

Following the advice in the Wubi guide 
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

I downloaded wubi-add-virtual-disk. Because my /usr folder is the large one, I tried to move it to a dedicated virtual disk by typing

sudo sh wubi-add-virtual-disk /usr 5000

(/usr had only been 2.1GB in size at that stage, so 5GB should be plenty of space). 

The script ran and indicated that it was successful, and I tried to shut down my computer. However it didn't cleanly shut down, but kept printing hundreds of messages

XXXX.xxxxx bad: scheduling from the idle thread. 

where the XXXX.xxxxx were numbers which seemed to keep increasing. 

After some time the computer would not stop doing this, and after trying a few keyboard commands to shut it down, I eventually had to hard reboot.

Now when I try to boot into ubuntu, I get past the initial ubuntu visual screen (the one with the black bar at the bottom that fills with orange as the system starts up), however the subsequent terminal screen output gives lots of messages that different files in /usr were not found, and stops at some stage. 

I have been able to hit ESC early in the boot process and boot in safe mode, where I get a terminal. Looking at the directory structure, I have both a /usr and a /usr.backup folder. Figuring that the problem might be fixed if I remove /usr and rename /usr.backup to /usr, I have tried to 
rm -r /usr
however the terminal tells me that this cannot be done, because files in /usr are in use.

Any ideas on how to fix this?

Thanks.

---

### Post by gazD on 2009-03-24
I think I have fixed this - it seems trying to run that script as I did was a very bad idea though.

Logging in through the terminal in recovery mode, I discovered that the newly created /usr folder had nothing in it. So I went to the /usr.backup folder, and copied every folder in it to /usr.

I was then able to reboot into the desktop. However, a new problem emerged, in that sudo no longer worked, but failed with a
sudo: must be setuid root

From searching the web, I found that this could be fixed by logging in as root through recovery mode again, and typing 
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
 
So far, things seem to be normal again - I hope.

---

### Post by cheribibi on 2011-04-28
Thank you so much gazD !

I would just sugget to use rsync to copy directories and files from /usr.backup to the new /usr tree, that is :```
cd /usr.backup 
./bin/sudo ./bin/rsync -av --exclude=./gvfs * /usr
```And I'd say you then probably won't need to chown and chmod /usr/bin/sudo as you mentionned.

---

