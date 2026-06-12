---
title: "Can't install ATI Radeon HD 5770 drivers properly on Ubuntu 12.10"
date: 2013-03-18
forum: Hardware
---

### Post by Hyper Tails on 2013-03-18
Hey guys;

I have an ATI Radeon HD 5770 graphics card in my computer. I want to install its driver in Ubuntu because I want to run Steam and play Team Fortress 2 while using Ubuntu without having to reboot my entire machine into Windows to do it. (I have 2 harddrives)

However, trying to install the drivers onto my Ubuntu system has been the worst yet from my history of using Ubuntu. If I install it, and it says it's complete, when I reboot the system, I get no Unity desktop. When I download the drivers from its offical site and run it in Terminal, I keep getting error messages saying in the picture below.

Any help will be thanked.

PS: I made an thread about what my next graphics card should be, it'll be an Nvida; This will be the last ATI card I buy.[ATTACH=CONFIG]240333[/ATTACH]

---

### Post by Ximaceo on 2013-03-19
Hi Hyper Tails, 

This is how I do:
-First full update Ubuntu.
-Download AMD Catalyst 13.1 Propietary driver from: [http://support.amd.com/us/gpudownloa...eon_linux.aspx]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")
-Unzip video driver. A new file .run will be created.
-Then click right botton on the file .run and click again on Properties.
-You will open a new window. Then follow these steps:
-Select the Permission tab and click on 'to allow execute the file as a program'
-Now double click on the file .run
-Choose the option to run in terminal and install.

Works fine for me.

Please mind that Im spanish and this is a traslation :wink:

You can also see this thread: [http://ubuntuforums.org/showthread.php?t=2126611](http://ubuntuforums.org/showthread.php?t=2126611)

---

### Post by Hyper Tails on 2013-03-19
The message I got earilier still shows up after doing the following steps you've given me.

PS: Your traslations are very good!

---

### Post by QIII on 2013-03-19
Remove the driver.

Before you attempt to reinstall it, install linux-headers-generic.

---

### Post by Hyper Tails on 2013-03-19
Got it working now!
Thank you so much! :)

I hope it also applies towards Ubuntu 13.04

---

### Post by Hyper Tails on 2013-03-19
UPDATE: After installing Steam, and trying to launch Team Fortress 2, I get this message: [ATTACH=CONFIG]240353[/ATTACH]

---

### Post by Hyper Tails on 2013-03-20
Sorry, I had to bump this.

---

### Post by Hyper Tails on 2013-03-22
Second bump. Dang.

---

### Post by QIII on 2013-03-22
A bump a day is good.

I did a little checking around.  There seem to be some common Steam issues.  They appear to involve older cards, but your problem may be similar.

How about starting a new thread in Gaming and Leisure with a title like "ATI, OpenGL and Steam problem"

---

