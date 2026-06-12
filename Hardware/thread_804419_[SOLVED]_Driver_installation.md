---
title: "[SOLVED] Driver installation"
date: 2008-05-23
forum: Hardware
---

### Post by PhilCash on 2008-05-23
G'day All,

Can someone push me in the right direction please? I need to know how to install additional drivers.
I have a Benq JoyBook 7000, which is running Hardy really well. 
The built in Texas instruments card reader does not work. I have located what I understand to be a driver for it and downloaded it from [http://prdownload.berlios.de/tifmxx/tifm-0.8e.tar.bz2](http://prdownload.berlios.de/tifmxx/tifm-0.8e.tar.bz2)
Double clicking this file opens the archive and shows me the contents... 

I've got no idea what to do with the file now.
Can someone tell me how to install this driver please?

Cheers,
Phil
Coming up next...how to get it to switch between internal and external monitors...any hints gratefully accepted.

---

### Post by itix on 2008-05-24
Welcome to the rather painful procedure called compiling. It's due to the fact that people don't bother packaging their stuff.
Now, lets begin shall we?

**1) Extract**
Extract your files to some convenient location (doesn't really matter where since we're going to delete the folder afterwards).

**2) Navigate to your folder with the terminal**
The terminal's located under *applications => acessories => terminal*. The terminal always start at your home folder. Type cd (which means change directory) without hitting enter. Go to your folder directly above where you extracted the files from the archive through the file browser (which is called nautilus). Drag the folder where you extracted your files to the terminal. Hit enter.

**3 a) Compile and install**
You might experience problems with this part, so first, make sure that you have the package called build-essential installed. You can find it under *system => administration => synaptic package manager*. Just click on the first package in the list and start typing buil... and it'll show up. If it's installed, there should be this green box in front of it. If not, there's a white box. Install it by clicking on the white box and choose install, and then click apply.

**3 b) Compile and install**
Now that you have the copiling set, lets install the driver. Go to your terminal again. It should still be set to the directory where your files are extreacted. type *sudo ./configure* and hit enter. You will be prompted for a password. Don't worry abou the fact that nothing shows up as you type (stars or dots), just enter your password and hit enter. A lot of text should hopefully at this piont roll up the screen. When this text is done, type *sudo make* and more text should be running up the screen. Now type *sudo make install* which will install the drivers on the system (with even more rolling text). Hopefully, this crucial part should have gone without errors. If not, notify me and I'll try to help

**4) Cleaning up**
Now, let's remove the files you extracted. They will now be owned by something called root, we will therefor have to change the ownership back to you. Type *cd ..* (cd period period) (this will take you to the folder directly above the extracted files folder). Then type *ls* and find the name of the folder you extracted the files to in the list. Then type *sudo chown -R **your username** blankspace **the foldername***. Let's give you an exaple; my user name is itix and my folder name is argh. I will then type *sudo chown -R itix argh*.
Now you can just use nautilus to delete the folder, hopefully without any problems. 


That should have been it. Your drivers should now have been installed. Please post any problems you might have and I'll help accordingly. One more thing; don't blame linux for this. It's the guy who created the drivers who didn't package them accordingly. Packaged things are even easier to install on linux than on windows. Just one click and one password entry.

---

### Post by PhilCash on 2008-06-11
G'day itix,

Thanks for your assistance so far, I hope you're still around... I've been resolving another problem with updates failing over the last week and having fixed that am just getting back to looking at installing these drivers.
I've followed your instructions, including installing build-essential, to 3b. "type sudo ./configure and hit enter", and am stuck there. The response I get to 
sudo ./configure
is 
sudo: ./configure: command not found
(the first time it asks for a password of course)
if I try just
./configure
I get
bash: ./configure: No such file or directory
I'm not yet up on the Linux command line unfortunately, so I'm a bit stumped.
I have extracted the files to a folder on my desk top called 'new', and my command prompt reads philcash@phil-laptop:~/Desktop/new$, and running ls lists the sub directory and files in that directory: (linux (the sub directory) Makefile tifm_7xx1.c tifm_core.c tifm_sd.c).
Any instructions, hints, and tips would be most welcome.

cheers,
Phil

---

### Post by Sef on 2008-06-11
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by itix on 2008-06-11
Ooops, my bad... :oops:
It didn't need configuring. Just skip ./configure and type *[COLOR="Green"]make[/COLOR]* and then [COLOR="Green"]*sudo make install*[/COLOR] on step 3b.

Most source installations have a configure file to configure.... something. I haven't found out exactly what though.

I'd like to change some bits in 4 as well since there is an easier way of deleting the folder. Just type *[COLOR="Green"]sudo nautilus[/COLOR]* and navigate to it and delete it.

---

### Post by itix on 2008-06-11
I hope it installs ok, because on my machine, *make* returns errors.

---

### Post by PhilCash on 2008-06-11
Hmmm...make errors...incompatible pointer types, initialisation of incompatible pointer types, undeclared functions...must think harder now...
I suppose there's no way to figure out if the files are actually complete or correct other than going back to their source. I'll keep digging...
Thanks anyway.
Thanks also to Sef, I'll dig into it.

cheers,
Phil

---

### Post by PhilCash on 2008-06-18
G'day Again,

Well, I've done some more digging...and learning...
The driver package I tried was tifm_7xx1 ver 0.8, and I've found statements on the development web site that it is not compatible with Kernel 2.6.24.

I've found tifm_7xx1.c for Kernel 2.6.25 and tifm_core.c for Kernel 2.6.24 at [http://www.linuxhq.com/](http://www.linuxhq.com/)... but am unsure as to the procedure for installing drivers that are provided as just source code. Do I simply replace the files of the same name in the version 0.8 package I tried before and go through the configure, make, make install routine? My current kernel is 2.6.24-18-generic (Ubuntu 8.04), are there likely to be any problems installing drivers released for 2.6.25 on my version?

Further; I've come across a mention that this device was supported in Ubuntu 6 out of the box. Is it possible that Ubuntu 8.04 should be able to detect the device and install a driver automatically? If so, it hasn't; how do I go about kick starting the process?

The device I'm on about is reported by lshw as:
*-storage UNCLAIMED
description: Mass Storage controller
product: PCIxx21 Integrated FlashMedia Controller
vendor: Texas Instruments 
physical id: 9.3
bus info:pci@000:02:09:3
version: 00
width: 32 bits
clock: 33MHz
capabilities: storage pm bus_master cap_list
configuration: latency=128 maxlatency=4 mingnt=7

lsmod does not show any drivers that look like they belong to this device.

I've tried both Sony MS and SanDisk SD cards and neither are noticed.

Cheers,
Phil

---

### Post by PhilCash on 2008-06-18
Now here's a turn up for the books...

I just rebooted after the latest updates with an SD card in the reader, and it mounted all by itself! So Ubuntu 8.04 does natively support the device (perhaps with caveats).

Unmounting, removing, and re-inserting got it to mount again; several times.
Sony MS still wont mount though (although the reader access light comes on)... Not even after rebooting with the MS in the reader. 
SD cards still work & uSD+adapter card works too.

Thank you for your support and efforts to assist me with this. The journey has been enlightening, and I've learned much along the way.

Cheers,
Phil

---

