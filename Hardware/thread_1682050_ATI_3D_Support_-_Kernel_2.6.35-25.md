---
title: "ATI 3D Support - Kernel 2.6.35-25"
date: 2011-02-05
forum: Hardware
---

### Post by r5r4y on 2011-02-05
Hello,
I've upgraded my kernel to 2.6.35-25, I used this PPA: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

To install the latest drivers, system is up and running fine but there is no 3D suppotr...

Hmm... I've tried to install the driver from the ATI site and now my system does not start at all [only recovery mode]. 

My graphic card is HD4890...

What can I do to solve this?

---

### Post by waynefoutz on 2011-02-05
First, remove the ATI drivers you installed.\


[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")


```
sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```

Or you could simply reinstall.

After you do that, and get your desktop back, add this PPA to your software sources:

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
```

Then use update manager and install all the new updates this PPA provides. You should see a HUGE improvement.

---

### Post by r5r4y on 2011-02-05
> **waynefoutz said:**
> First, remove the ATI drivers you installed.\


[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")


```
sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```

Or you could simply reinstall.

After you do that, and get your desktop back, add this PPA to your software sources:

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
```

Then use update manager and install all the new updates this PPA provides. You should see a HUGE improvement.

Thanks a lot for the help. 

after running the first command sudo apt-get remove --purge fglrx*
the system got back up and the driver from ATI site works great. 

I guess the problem was fglrx-modaliases.
Should I add the PPA you gave me anyway? Does it improve a lot?

---

### Post by waynefoutz on 2011-02-05
It improved mine. I have an older ATI card, a Mobility X1270, running 10.04, and the open source radeon drivers out of the box had a lot of apllications such as google earth and 3d games, not working at all. The PPA willl give you a feed to the latest open source radeon drivers. On my rig, it made a huge difference. But, if you are satisfied with what you have now, the old addage of "if it ain't broke, don't fix it," is an understandable position to take.

---

### Post by waynefoutz on 2011-02-05
It improved mine. I have an older ATI card, a Mobility X1270, running 10.04, and the drivers out of the box had a lot of apllications such as google earth and 3d games, not working at all. The PPA willl give you a feed to the latest open source radeon drivers. On my rig, it made a huge difference. But, if you are satisfied with what you have now, the old addage of "if it ain't broke, don't fix it," is an understandable position to take. 

When you purged fglrx, you essentially removed the proprietary drivers you downloaded from ATI's site. You should be running the open source "radeon" driver now. If you are running the proprietary driver, you DO NOT want to add that ppa.


sorry for the double post, i thought I was editing the first one..

---

