---
title: "NVIDIA-Linux-x86_64-180.51-pkg2.run ?????"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by tardiaf on 2009-05-21
I am dying here - I have read all over the place how to install this after i downloaded the file but I am in the total dark here. Can someone help me? My current graphics card is dying an I have this new one but I need to install the driver for it to work. I do not know how to run and install this. also, I dont even know if I am on 32bit or 64...I think its 64? Either way, I have this graphics card in a box and need to get this bad boy in here. 

someone please help me install this! =)

---

### Post by oldos2er on 2009-05-21
Usually you'd go to System, Administration, Hardware Drivers to install video drivers.

---

### Post by logos34 on 2009-05-21
try olderos2er method first.  If no go, post back

to find out 64- or 32-bit:

uname -a

---

### Post by googlegot on 2009-05-21
To find out if you are using 32 or 64 bit ubuntu type this in terminal:

uname -m

It will output your architecture based on your kernel type.

You have downloaded the 64 bit version of your drivers, if you do not have the 64 bit version of ubuntu installed, this package will fail, and you will need to download the 32 bit version. 

To install the drivers normally, go to System>Administration>Hardware Drivers and enable the Nvidia driver.  If you want to use the driver you downloaded follow the steps I have listed below.

Assuming you have a 64 bit version of ubuntu installed:

1. In terminal navigate to the directory you downloaded the file to.

More than likely it was downloaded to your desktop if you used  firefox so type this in terminal:

cd /home/*your user name*/Desktop

2. Give the installer executable privileges.

chmod +x NVIDIA-Linux-x86_64-180.51-pkg2.run

3. Execute the installer.

sudo ./NVIDIA-Linux-x86_64-180.51-pkg2.run

4. Follow the instructions on screen.

---

