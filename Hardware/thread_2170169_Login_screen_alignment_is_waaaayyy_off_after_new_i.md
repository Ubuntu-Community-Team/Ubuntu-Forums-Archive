---
title: "Login screen alignment is waaaayyy off after new install (HIS Radeon HD 6570 Silence)"
date: 2013-08-25
forum: Hardware
---

### Post by knud200 on 2013-08-25
I have installed the Ubuntu 13.04 amd64-version on a brand new computer. I have bought a similar computer for my father a few weeks ago with the only difference being the graphic card and the power supply. His didn't have any problems after installation, so I suspect it is the driver for the graphic card. Here is a screenshot of how it looks like:


[IMG]http://i.imgur.com/oDiNQorh.jpg[/IMG]

So this is much more than just adjusting the alignment with a button on the monitor. What has been installed is the 64-bit version of Ubuntu (the same as my father's installation). But here the graphic card is a "HIS Radeon HD 6570 Silence". During the setup, I selected the 3rd-party software and to automatically download updates during installation. Now I can't get past the login screen, but can get to a command prompt by using the CTRL+Alt+F2. Does anyone have an idea of how to fix this?

---

### Post by knud200 on 2013-08-25
The problem has been solved. I needed to manually download and install the driver. Here is what to do:

[LIST=1]
[*]Boot up the new installation to the login screen.
[*]Press Ctrl+Alt+F2 to get to a command prompt and log in with your credentials.
[*]Download the driver
```
wget http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13-4-linux-x86.x86_64.zip
```
[*]Unzip the driver
```
unzip amd-driver-installer-catalyst-13-4-linux-x86.x86_64.zip
```
[*]Make the script executable
```
chmod u+x amd-driver-installer-catalyst-13-4-x86.x86_64.run
```
[*]Run the script with administrator privileges. I followed the recommended settings, basically pressing enter the whole time.
```
sudo ./amd-driver-installer-catalyst-13-4-x86.x86_64.run
```
[*]Reboot the computer. After startup, the new Ubuntu installation should work.
```
sudo reboot
```
[/LIST]

---

