---
title: "Upgrade problems with KDE 4.2 in Kubuntu 8.10"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by xlearner on 2009-04-03
Hello all,

I tried to upgrade to KDe 4.2 on Kubuntu 8.10. I was following the instructions mentioned : [http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2). 

But I think I did not follow the instruction correctly. KDE 4.2 was not properly installed. Probably I did not unistall all the incompatible packages. Right now my system is in a mess. The KDE manager has failed completely. Earlier I had installed Gnome as well on my machine. So I am working on Gnome now. In fact when I login, I don't even see KDE as an option. I believe my system removed it automatically since it was not working. I don't know what to do at this point. 

Then I found the following thread: [http://ubuntuforums.org/archive/index.php/t-1062869.html](http://ubuntuforums.org/archive/index.php/t-1062869.html). I tried following the steps in this thread, but of no avail. I did, sudo apt-get update && sudo apt-get upgrade. Everything seemed fine.

Then I observed that my sound card stopped working as well. So I tried fixing that by looking at this page: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting).

I entered the command on terminal:  sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic. The output is as follows:

sat@sat-laptop:~$ sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.27-11-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.27-11-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

sat@sat-laptop:~$ 

So I think the headers somehow got corrupted. So does anyone have any suggestions to help me? Let me know.

Thanks

---

### Post by miklcct on 2009-04-07
sorry, there is no linux-ubuntu-modules in intrepid

---

### Post by CyberMando on 2009-04-07
Assuming you have the correct sources in your sources.list file (you probably do) run
sudo aptitude update
and then 
sudo aptitude install kde
This should bring in a lot of packages and get KDE operational again. If you want KDM you will need to install it with
sudo aptitude install kdm
Unless you are intentionally using GDM you probably do want KDM.

---

