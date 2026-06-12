---
title: "Drivers for nvidia gtx 650 ti"
date: 2015-01-12
forum: Hardware
---

### Post by dridrilamenace on 2015-01-12
Hello,
Here's my problem: I need to remove the graphic board of my  computer, because otherwise every monitor don't recognize the computer  (they do as if the computer was shut down). I know the reason why it's  like this: I need the right driver and make it work.
So what is the right driver for an nvidia gtx 650 ti and how to install it on the computer?
Thanks beforehand for your help ;)
P.S.: I have ubuntu 14.04.


EDIT: I just forgot to mention that I'm pretty new with Ubuntu.

---

### Post by oldfred on 2015-01-12
I do not think that card is so new that you have to use a ppa to get a more recent version than is in Ubuntu's repository.
There are three ways to install nVidia drivers, the Ubuntu repository using System settings and other software and drivers tab. Use a ppa which has the newest drivers from nVidia or directly download from nVidia. The direct download is not recommended as you have to re-run processes on every kernel update. Best to use Ubuntu repository unless you have to have the very newest from nVidia, then use a ppa.

       nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

Current version's repository has never versions than this shows, but shows the install process.

 [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

[http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)


 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended 

   #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
What is installed
dkms status

---

### Post by dridrilamenace on 2015-01-13
[SIZE=2]Thank you for your answer, the driver is the version 340.65, but after the download, I have to make it [COLOR=#000000][FONT=Arial]an executable file[/FONT][/COLOR]. How to do this?[/SIZE]

---

### Post by oldfred on 2015-01-13
You then are downloading from the nVidia site. That really is not recommended. Or every kernel update will require resetting the driver to work with new kernel.

You should be able to use the newest version in Ubuntu repository which is one or two versions older. If you want the 340.xx which now is legacy or will only get security updates from nVidia.

I have seen two different ppa suggested. xorg-edgers & mamarley
You just add those ppa to the repository sources and since a newer version, it will update from the ppa.

 Install Nvidia 340.24 from ppa:xorg-edgers/ppa
[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)
14.04 drivers for Nvidia GeForce GT 730 desktop board - 
[http://ubuntuforums.org/showthread.php?t=2240702](http://ubuntuforums.org/showthread.php?t=2240702)
PPA for nVidia mamarley ppas
[http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945](http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945)
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
All the current drivers xorg-edgers PPA
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)

---

### Post by dridrilamenace on 2015-01-13
Just two stupid questions:
Are the two PPA that you sugest used with the nvidia driver from their site?
If yes what is the best way to download the apropriate driver according to you (plus the easiest method to do it)?
Sorry if it seems stupid: I'm a noob with linux :(

---

### Post by oldfred on 2015-01-13
I do not know if one ppa is better than the other.
But they take the nVidia drivers and make them just like installing from Ubuntu repository. Much easier way.

If you have installed any nVidia driver be sure to uninstall/purge first. Drivers conflict otherwise.

Some of the links have details on installing, I have not done it. You add ppa and update.

---

### Post by dridrilamenace on 2015-01-14
Ok, I'll try what you sugested, and I'll tell you if it works :)

---

### Post by dridrilamenace on 2015-01-14
I tried with the first link taht you gave me and now I'm able to run my computer with the graphic board and i can play. Thanks a lot :)

---

