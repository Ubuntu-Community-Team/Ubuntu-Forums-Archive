---
title: "Installing Drivers NewBie"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by sundeniro on 2009-07-20
Hi Guys

i have installed the latest Ubuntu my first linux install however my wifi usb dongle isn't functioning. I was able to find comand liusb to confirm that it is connected.

The manufacturers offer 2 linux drivers available from the manufacturer

Safecom SWLUT-54125 is the model number of the USb

I have no idea though how to install the drivers all help very gratefull received

---

### Post by mikewhatever on 2009-07-20
Can you link to the page with the drivers for Linux. From a quick look at [the device's page]("http://safecom.cn/code/sub/category.asp?prdid=318&subcatid=41#"), it seems like a Windows only gadget.

---

### Post by rainwalker on 2009-07-20
EDIT: The page with the driver has instructions: [http://safecom.cn/code/product/WLAN/SWMULZ-5400/manual/SWMULZ-5400-Linux-UserGuide.pdf](http://safecom.cn/code/product/WLAN/SWMULZ-5400/manual/SWMULZ-5400-Linux-UserGuide.pdf)
Read that, it looks like you have to edit the makefile depending on your kernel version, which you can find out under System > Administration > System Monitor under the "General" tab (Ubuntu 9.04 uses the 2.6 kernel).

If you download the Linux driver (I would go with version 2 because it's probably newer/better), it gives you the file "V2-Linux-Driver.gz". This is an archive with the driver in it, so go to wherever you saved it and right-click on it and choose "Extract here". For some reason they archived and archive, as this will give you another one called "V2-Linux-Driver", so just right-click on it again and choose "Extract here". This will give you a folder called "ZD1211LnxDrv_2_6_0_0". There are two folders and some other files inside of that folder, on of which is a makefile. If this works how I think it does, you should be able to open a terminal, use the command "cd" to change to wherever this directory is. For example, for me, I would run ```
cd /home/riley/Desktop/ZD1211LnxDrv_2_6_0_0 
``` because I saved all this to my Desktop. Once you're in that directory, you should be able to run the commands "make" and then "make install" and it should install the drivers.

---

### Post by Sef on 2009-07-20
> Once you're in that directory, you should be able to run the commands "make" and then "make install" and it should install the drivers.

Read [How to Install Anything in Ubuntu]("http://amitech.50webs.com/installing/index.php.html")

---

### Post by sundeniro on 2009-07-21
Hi Guys

Thanks for trying to help

decided after trying to install the linux driver that I would give ndiswrapper a try using the windows driver.

althou lsusb lists the device after I install the win driver using the graphical interface it shows no hardware detecetd.

Any thoughts

P.S. lsusb lists the device as d-link 07b8:b21a

---

### Post by sundeniro on 2009-07-21
Thanks for all the help.

I managed to get things up and running by copying over the files from XP

---

