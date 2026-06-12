---
title: "Need SIS Driver 661/741/760 for any version of Lubuntu. Help."
date: 2017-09-17
forum: Hardware
---

### Post by flamingfox on 2017-09-17
I had the recent version of Lubuntu 17.04 installed on my old Travelmate 2310, but it has one of those cursed SIS graphics cards. Specifically, the 661/741/760 card. I've been looking around the internet for the past 2 weeks. And I found some old threads pertaining to either older versions of Lubuntu (16.04, 14.04, 12.04, etc) or other versions of the card (671/771). I've been trying to install the SIS driver using the old hardware thread, but that got me nowhere since the packages are not being properly unpacked (deprecated/broken lines of code). I then tried loading up an 14.04, since that was the last successful version to have had SIS cards working, but that ended up not working either.

Can someone give me a 100% working SIS driver package, its associated Lubuntu version, and a proper how-to setup of the driver (assuming that there have been 0 dependencies, other than the defaults, installed).

Thanks in advance.

---

### Post by mörgæs on 2017-09-18
The package has been removed from 17.04 due to security reasons, as can be seen [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276/") (post eight).

If you accept the possible security problem it's probably an easier approach to begin with 16.04.

---

### Post by flamingfox on 2017-09-22
Thanks for the reply and sorry for the delay.

I have fresh installed Lubuntu 16.04.3 and currently trying to install the dependencies it needs for xserver-xorg-video-sis. But currently there is a problem when trying to install the dependencies:

```
experiment@OlTravelmate:~/Downloads$ sudo apt-get install xserver-xorg-video-sis
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-sis is already the newest version (1:0.10.7-0ubuntu6).
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 xserver-xorg-video-sis : Depends: xorg-video-abi-15 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

I am trying to find xorg-video-abi-15, but can't seem to find it anywhere. Any pointers?

EDIT: Just found out that it needs xorg-video-abi-15 to work, but what I am using is abi-20.
```
experiment@OlTravelmate:~/Downloads$ sudo apt-get install xorg-video-abi-20
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xserver-xorg-core' instead of 'xorg-video-abi-20'
xserver-xorg-core is already the newest version (2:1.18.4-0ubuntu0.4).
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 xserver-xorg-video-sis : Depends: xorg-video-abi-15 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by mörgæs on 2017-09-23
And what did

> **flamingfox said:**
> 
```
Try 'apt-get -f install'
```

yield?

---

### Post by flamingfox on 2017-09-23
```
workinprogress@OlTravelmate:~$ sudo apt-get install xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxatracker2 x11-apps x11-session-utils xinit xinput
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  xfonts-100dpi | xfonts-75dpi xfonts-scalable
The following packages will be REMOVED:
  lubuntu-core lubuntu-desktop xorg xserver-xorg-core-hwe-16.04
  xserver-xorg-hwe-16.04 xserver-xorg-input-all-hwe-16.04
  xserver-xorg-input-evdev-hwe-16.04 xserver-xorg-input-synaptics-hwe-16.04
  xserver-xorg-input-wacom-hwe-16.04 xserver-xorg-video-all-hwe-16.04
  xserver-xorg-video-amdgpu-hwe-16.04 xserver-xorg-video-ati-hwe-16.04
  xserver-xorg-video-fbdev-hwe-16.04 xserver-xorg-video-intel-hwe-16.04
  xserver-xorg-video-nouveau-hwe-16.04 xserver-xorg-video-radeon-hwe-16.04
  xserver-xorg-video-vesa-hwe-16.04 xserver-xorg-video-vmware-hwe-16.04
The following NEW packages will be installed:
  xserver-xorg-core
0 upgraded, 1 newly installed, 18 to remove and 14 not upgraded.
Need to get 1,411 kB of archives.
After this operation, 5,607 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
workinprogress@OlTravelmate:~$ sudo dpkg -i /home/workinprogress/Downloads/xserver-xorg-video-sis_0.10.7-0ubuntu6_i386.deb 
Selecting previously unselected package xserver-xorg-video-sis.
(Reading database ... 162807 files and directories currently installed.)
Preparing to unpack .../xserver-xorg-video-sis_0.10.7-0ubuntu6_i386.deb ...
Unpacking xserver-xorg-video-sis (1:0.10.7-0ubuntu6) ...
dpkg: dependency problems prevent configuration of xserver-xorg-video-sis:
 xserver-xorg-video-sis depends on xorg-video-abi-15; however:
  Package xorg-video-abi-15 is not installed.
 xserver-xorg-video-sis depends on xserver-xorg-core (>= 2:1.14.99.902); however:
  Package xserver-xorg-core is not installed.
  Version of xserver-xorg-core on system, provided by xserver-xorg-core-hwe-16.04:i386, is <none>.

dpkg: error processing package xserver-xorg-video-sis (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 xserver-xorg-video-sis
workinprogress@OlTravelmate:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  xserver-xorg-video-sis
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
1 not fully installed or removed.
After this operation, 655 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
workinprogress@OlTravelmate:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 xserver-xorg-video-sis : Depends: xorg-video-abi-15 but it is not installable
                          Depends: xserver-xorg-core (>= 2:1.14.99.902)
E: Unmet dependencies. Try using -f.
```

Forcing a install of core would result in removing so many lubuntu files that it requires me to reinstall the OS. So I can't force install xserver-xorg-core.

I don't think 16.04.3 can accept a sis driver. I think I may have to downgrade further. Unless you can locate for me a proper sis driver package that can work with either 16.04.3 or 17.04... Let me know. Also thanks for your assistance :)

---

### Post by mörgæs on 2017-09-24
I don't know if there is difference between 16.04.1 and 16.04.3 regarding SIS support but yes, it's worth a try. 

I happen to have tested [similar hardware]("https://ubuntuforums.org/showthread.php?t=2252413&page=3&p=13589000&viewfull=1#post13589000") under Lubuntu 16.04.1 with good results.

---

### Post by flamingfox on 2017-09-24
Alright, so I was having some installation issues with 16.04.1 (Graphical Artifacts when doing the installation process), so I went further and installed 16.04.

I was trying to install the xserver-xorg-video-sis, but it still says that xserver-xorg-abi-15 needs to be installed, which should be part of the xserver-xorg-core package. I tried installing an older version of core, but it resulted in broken dependencies and locked my computer.

I think its fair to say that my computer is defunct and I can no longer use the SIS video drivers. Thanks for your assistance, but its time to put this computer down... For a while at least. If you do end up having sis driver work in 17.04, please toss a message here or PM. I would appreciate it :)

---

### Post by mörgæs on 2017-09-25
It's unlikely that I will find a solution. Best you can do is to post in the thread to which I linked. People there know more about the problem than me.

---

### Post by Yellow Pasque on 2017-09-25
You are trying to install an old version (0.10.7) that doesn't support newer Xservers. Try a newer version:

```
sudo apt-get install build-essential xorg-dev xutils-dev automake libtool
cd ~/   #or whatever directory you want to use for this build
wget http://xorg.freedesktop.org/releases/individual/driver/xf86-video-sis-0.10.9.tar.bz2
tar -xjf xf86-video-sis-0.10.9.tar.bz2
cd xf86-video-sis-0.10.9/
autoconf
automake
./configure --prefix=/usr/local
make
sudo make install
```

---

