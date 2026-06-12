---
title: "Drivers problems- noob"
date: 2008-04-18
forum: Hardware &amp; Laptops
---

### Post by Xander_Evil65 on 2008-04-18
Hi All ..

I'm new to this so sorry if i ask some dumb questions, i installed ubunu 7.10 just yesterday

First, my specs
AMD 5200+ (2.6Ghz x 2)
MSI K9N nForce 570 ultra-2F mobo
4GB Ram (1 x 4) Kingeston
MSI 7600GS 256MB onboard
WD 320GB HDD
Dual boot (ubuntu 7.10 64-bit - Win XP prof. 64-bit)


i downloaded the GeForce driver from nvidia.com, double checked it's for linux 64-bit, followed the instructions but it doesn't find the driver, and i mean it's like it doesn't know it's destination, and ofcourse i have no idea what i'm typing in the terminal so i can't edit to fit my situation
here's the instructions from nvidia.com
**Type "sh NVIDIA-Linux-x86_64-169.12-pkg2.run" to install the driver. **
i type that and the terminal say that sh can't find the file


i also tried to install Autodesk Maya 2008 which is the first reason why i installed ubuntu, i googled on how to install it and here's the instructions

[B]1 Install RPM Package Manager:
sudo apt-get install rpm
sudo mkdir -p /var/lib/rpm

2 Install Maya-RPMs
cd linux-amd64/
sudo rpm -ivh --nodeps AWCommon-10.80-15.x86_64.rpm Maya2008_0_64-2008.0-134.x86_64.rpm

3 Install csh-shell
sudo apt-get install csh

4 Create Maya-Temp directory
sudo mkdir /usr/tmp
sudo chmod 777 /usr/tmp

5 Start Maya
cd /usr/autodesk/maya/bin
csh maya[/B]

it also gets to the "cd linux-amd64/" line and the terminal says it can't find it


last, i can't find linux driver for the motherboard, so nothing really works :)
no internet connection, sound, anything
also i have a dual monitor setup, ubunto uses only one and turns the other one off, but i think that's because of the vga driver

that's for now, i have a pen pad which i don't know if it works or not but i have some more important issues to worry about now :lolflag:

Thanks in advance

---

### Post by Xander_Evil65 on 2008-04-18
well,  got to open the nvidia driver by typing
sudo -s
in the terminal, which makes me use root account
i couldn't open the file too, but when i drag and drop it in the terminal it runs, then it tells me that i've got to close the "x server" to install the driver
i opened the restricted drivers window, and tried to install from there also no good, it tells me that there's no driver
i tried another method that i found on some site

[B]Open a terminal and type sudo apt-get update 
Type sudo apt-get install nvidia-glx 
Type sudo apt-get upgrade 
Type sudo dpkg-reconfigure xserver-xorg 
Select the nvidia driver from the X server driver list and follow the on-screen steps to complete the configuration 
Once finished with the configuration, hold down Ctrl+Alt+Backspace to restart X server. You should be presented with a nice NVIDIA splash screen signaling that the driver is installed and working 
You can test this in the terminal by typing glxinfo | grep direct (the output should be direct rendering: yes) 
You can also type glxgears to watch your card at work [/B]

it gets to the second line where it should access the driver and tells me that it can't find it, i tried to change the name "nvidia-glx" to the actual file name, it didn't work, tried to rename the file itself to nvidia-glx, didn't work either

any help plz ..

---

### Post by gigantorpdx on 2008-04-19
Hello All- 

I am all new to this also and was having the same problem as mention in the previous post so I follow the directions as mentioned.

[B]Open a terminal and type sudo apt-get update
Type sudo apt-get install nvidia-glx
Type sudo apt-get upgrade
Type sudo dpkg-reconfigure xserver-xorg
Select the nvidia driver from the X server driver list and follow the on-screen steps to complete the configuration
Once finished with the configuration, hold down Ctrl+Alt+Backspace to restart X server. You should be presented with a nice NVIDIA splash screen signaling that the driver is installed and working
You can test this in the terminal by typing glxinfo | grep direct (the output should be direct rendering: yes)
You can also type glxgears to watch your card at work[/B]

Restarted the computer, I did not get the Nvidia splash screen, but I was able to check the box to enable the restricted driver, which I was not able to do before. It install some more packages. Restart.

At that point I was able to check the 3D effects in the System/Preferences/Appearances

Seems to be working.

Question through - Where did you find the original install information that I included in this post?

---

