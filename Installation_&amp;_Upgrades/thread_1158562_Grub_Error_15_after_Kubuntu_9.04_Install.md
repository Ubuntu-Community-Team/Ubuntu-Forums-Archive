---
title: "Grub Error 15 after Kubuntu 9.04 Install"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by UanarchyK on 2009-05-13
I have three partitions, 
sda1 10gb, 
sda3 200gb, and:
sda5 4gb

I installed the new Kubuntu release using manual partition settings with sda1 mounted to /, sda3 mounted to /home, and sda5 as swap. When I rebooted, GRUB gave an Error 15. 

I've spent a couple hours unsuccessfully trawling the internet. Everyone else who has received an Error 15 seems to have luck by typing find /boot/grub/stage1 into the grub prompt, or variants of that. No such luck for me.

Somebody please help! It appears my GRUB has disappeared and won't come back. I've tried doing the installation again and I'm certain my disc is fine. 

I've wasted a day backing up my data and re-partitioning my disk, and now my stupid GRUB won't boot the installation. :(

---

### Post by upchucky on 2009-05-13
Get Supergrub to set up/repair Grub here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

after you have downloaded and created the supergrub disk boot from it then use it to fix grub.

you must read the instructions carefully and understand them, google what you do not understand. You will not hurt anything with this but can get very confused if you do not understand what it does.

---

### Post by UanarchyK on 2009-05-14
SuperGrub doesn't seem to be doing anything because I don't have an initrd file

---

### Post by UanarchyK on 2009-05-14
I can now boot up to the login screen, but now my computer thinks it's called "rothera" and no longer recognizes my user name and password. 

SuperGrub and its documentation were basically 100% useless. There is obviously something going wrong with my installation and it's not installing an initrd.img or GRUB, but apparently no one else in the history of Google has had similar problems.

---

### Post by Zaphio on 2009-05-22
same problem here with both ubuntu 9.04 server and desktop and can't seem to find any usefull information on the topic. Initially I thought it had to do with the ext4 filesystem, but ext3 does exactly the same.

I am new to the server thing and I finally had the spirit to work on my server skills. failed miserably due to grub not loading properly, and since its a error 15, it probably points to a wrong disk/partition.

a potential solution is given on the following site and will try it later tonight:
[https://answers.launchpad.net/ubuntu/+question/71891](https://answers.launchpad.net/ubuntu/+question/71891) 

another site (in Dutch) which gave some info was, showing that xp and suse were started correctly, except starting ubuntu 9.04 giving error 15:
[http://forum.ubuntu-nl.org/installatie/error-15-in-grub-met-tripleboot/](http://forum.ubuntu-nl.org/installatie/error-15-in-grub-met-tripleboot/)

So the problem just may be in grub configuration in jaunty? 

Installing 8.10 desktop and then upgrading to 9.04 did work, but don't think this is the supreme way to solve the issue :P
Anyway, got the coming weekend dedicated to this matter, I need it solved for the sake of just getting it solved, it will give me sleepless night otherwise.

anyway,
ask me questions about linux in about a month, I will be your next guru :P

Kind regards,
zaph

---

### Post by pbhj on 2009-09-04
I had this problem too - error 15 appears to mean that files are missing. With me I needed to use a liveCD and alter the device.map file - full info of [fixing error 15 on kubuntu 9.0]("http://alicious.com/2009/grub-2-install-error-15/")4 for my problem.

---

### Post by presence1960 on 2009-09-04
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

