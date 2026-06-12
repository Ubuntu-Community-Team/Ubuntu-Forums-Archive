---
title: "Issue with External HDD."
date: 2020-05-06
forum: Hardware
---

### Post by moxiblu on 2020-05-06
Hello all! So I finally made the switch to Ubuntu from Windows this morning, and I'm in the process of installing everything that I need. I've got my Steam, wine, Lutris, etc. however the issue I'm having is my laptop has extremely limited space so I have an external hdd to pick up the slack. I used my hdd with windows first, so I have quite a few games/programs on it as is, but when I opened Lutris/battle.net I realized that I could use my hdd that already has a couple of the games downloaded (World of Warcraft, Starcraft 2) without having to download them again. However, my steam games are refusing to be downloaded to my external hdd because it's still formated for windows exfat. So I installed Gparted, and tried to change the size of the partition so I could reformat the other part of the HDD to ext4 in order to allow steam to install the games there. However, it won't let me resize, either with the slider-bar, the values, or by pressing the button because it's not recognized. 

"Unable to read the contents of this file system! Because of this some operations may be unavailable." Is the error I'm getting under the information tab. I guess my question is, is there a way to resize and reformat while keeping the windows contents because I'm going to need them anyway, or do I have to wipe it, reformat it and reinstall everything. I'm new with Ubuntu, so please be gentle and as informative as you can, ELI5 if you will. Thank you for your time.

---

### Post by CelticWarrior on 2020-05-06
[LIST=1]
[*]Install exFAT support: ```
sudo apt install exfat-fuse exfat-utils
```
[*]Make sure the partition to be resized is NOT mounted (you can use the right-click menu in Gparted to unmount it)
[/LIST]

---

### Post by yancek on 2020-05-06
Which partition are you trying to resize?  You can't resize a partition which is in use so if you want to make a change to the partition on which you have Ubuntu you need to use GParted which is on the Ubuntu install DVD/USB.  If that's not the problem, you need to be more specific on what you want.  An of course you need to install the software to access exfat.  I don't believe any Linux OS has those tools in a default install.

---

### Post by moxiblu on 2020-05-06
> **CelticWarrior said:**
> 
[LIST=1]
[*]Install exFAT support: ```
sudo apt install exfat-fuse exfat-utils
``` 
[*]Make sure the partition to be resized is NOT mounted (you can use the right-click menu in Gparted to unmount it) 
[/LIST]


I made sure it wasn't mounted and ran the command, there were no errors. However, when I tried to resize in gparted again it didn't allow me and there was still the same error: Unable to read the contents of this file system! Because of this some operations may be unavailable.

---

### Post by moxiblu on 2020-05-06
> **moxiblu said:**
> I made sure it wasn't mounted and ran the command, there were no errors. However, when I tried to resize in gparted again it didn't allow me and there was still the same error: Unable to read the contents of this file system! Because of this some operations may be unavailable.

I have a couple downloads on my ext. hdd that I want to keep, but I need to set a partition up on it that will allow my steam install to allow me to save and install there. So I need to partition like 200Gigs to ext4 while keeping part of the partition exfat. In my Gparted, it won't let me resize at all, be it through the slider bar, the values under it nor the button. It either doesn't move or is greyed out in the case of the button. I don't know how to explain better than that lol, though the previously recommended command SEEMS as though it would help solve the issue, but it still doesn't let me do it.

*EDIT* Damn, I totally thought I was editing my previous post, apologies for the double post.

*EDIT #2* I attached a picture as to what I mean, the slider bar does not move at all, even if I manually put in the size I want partitioned, the button is STILL grey.

---

### Post by CelticWarrior on 2020-05-06
According to the answers here [https://askubuntu.com/questions/999580/why-is-exfat-greyed-out-in-gparted](https://askubuntu.com/questions/999580/why-is-exfat-greyed-out-in-gparted) GParted doesn't support exFAT for anything other than moving or copying.
Another answer and comments said Disks (gnome-disks) supports it but I think it doesn't have advanced features like resizing which is what you want.
Lastly they mention KDE Partition Manager. That might (still) work, good luck.

Really, in the future, avoid exFAT.

---

### Post by moxiblu on 2020-05-06
> **CelticWarrior said:**
> According to the answers here [https://askubuntu.com/questions/999580/why-is-exfat-greyed-out-in-gparted](https://askubuntu.com/questions/999580/why-is-exfat-greyed-out-in-gparted) GParted doesn't support exFAT for anything other than moving or copying.
Another answer and comments said Disks (gnome-disks) supports it but I think it doesn't have advanced features like resizing which is what you want.
Lastly they mention KDE Partition Manager. That might (still) work, good luck.

Really, in the future, avoid exFAT.

I did another google search on KDE Partition Manager and got this: 1 Answer. Gparted and **KDE Partition Manager** do not **resize exfat** because there are no (command line) tools to **resize exfat**. The easiest thing you can do is to backup all data from your **exfat partition** and copy it back later after repartitioning.

So I think either way I'm doomed, well thank you for your help anyway, I was honestly just trying to save myself some time and figured there might be a workaround like with most things Linux. I appreciate your time and help regardless.

---

### Post by CelticWarrior on 2020-05-06
Too bad... :(

But if you have access to a modern Windows computer you can resize (shrink) it there and then do the rest in Ubuntu as originally planned.

---

