---
title: "GeForce GTX750ti with ubuntu 14.10"
date: 2014-10-28
forum: Hardware
---

### Post by rainbatt on 2014-10-28
Just installed the latest version of ubuntu 14.10 and have blurry fonts, unable to read, using geforce gtx750ti.
Anyone has the same problem or solutions?
Checked for additional drivers and there was none.

---

### Post by rainbatt on 2014-10-28
Solved.

[B]NVIDIA 340.46 driver for Linux

[/B][B]$ sudo add-apt-repository ppa:mamarley/nvidia
$ sudo apt-get update
$ sudo apt-get install nvidia-340[/B]

---

### Post by rainbatt on 2015-01-29
Just an update,

Install Nvidia Driver 334.21 in Ubuntu linux

sudo apt-get purge nvidia*; sudo apt-get install nvidia-319-updates-dev

You may switch to the recommended open-source driver in “Software & 
Updates -> Additional drivers” utility after restarted your computer.


Download the driver from the official links
[http://us.download.nvidia.com/XFree86/Linux-x86/334.21/NVIDIA-Linux-x86-334.21.run](http://us.download.nvidia.com/XFree86/Linux-x86/334.21/NVIDIA-Linux-x86-334.21.run)
[http://us.download.nvidia.com/XFree86/Linux-x86_64/334.21/NVIDIA-Linux-x86_64-334.21.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/334.21/NVIDIA-Linux-x86_64-334.21.run)

Press **Ctrl+Alt+F1** key combination on your keyboard to switch to command console and login.

Stop the graphic session with the appropriate command below:
sudo service lightdm stop     ## For the default LightDM
sudo service gdm stop     ## For the Gnome GDM
sudo service mdm stop     ## For the Linux Mint default MDM

Now give executable permission and start the installer, and finally follow the on-screen instructions to complete the process.
chmod +x ~/Downloads/NVIDIA-Linux-*-334.21.run && sudo sh ~/Downloads/NVIDIA-Linux-*-334.21.run


You may keep the installer file so that you can remove this driver 
via below command if for some reason this driver does not work properly:
sudo sh ~/Downloads/NVIDIA-Linux-*-334.21.run --uninstall

---

### Post by rainbatt on 2015-01-29
Another simpler way to update to latest 340,
                         [LEFT]
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get install ppa-purge
sudo apt-get update
sudo apt-get install nvidia-340
sudo apt-get install nvidia-340-uvm
[/LEFT]

---

### Post by rainbatt on 2015-01-29
From here,

[http://www.ubuntuupdates.org/ppa/xorg-edgers?dist=utopic](http://www.ubuntuupdates.org/ppa/xorg-edgers?dist=utopic)

---

### Post by rainbatt on 2015-01-29
[B][http://linuxg.net/how-to-install-the-nvidia-346-35-driver-on-ubuntu-14-10-ubuntu-14-04-and-derivative-systems-2/](http://linuxg.net/how-to-install-the-nvidia-346-35-driver-on-ubuntu-14-10-ubuntu-14-04-and-derivative-systems-2/)

How to Install / Upgrade to Nvidia 346.35 Driver in Ubuntu[/B]
$ sudo add-apt-repository ppa:xorg-edgers/ppa
$ sudo apt-get update
$ sudo apt-get install nvidia-346 nvidia-settings

---

