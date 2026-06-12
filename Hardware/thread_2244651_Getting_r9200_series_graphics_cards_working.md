---
title: "Getting r9200 series graphics cards working"
date: 2014-09-17
forum: Hardware
---

### Post by maxinstuff2 on 2014-09-17
**UPDATE - 26/05/2015**
As of a few days ago, the "OMEGA" release of fglrx is now in the repos. WINE dependancy issues also appear to be resolved. I found out because an auto-update tried to "upgrade" the packages and completely borked my display. So, I'll insert a quick little guide on how to fix that issue for anybody else that it happened to. You can also follow this to install fresh, starting from step 3.

I should also note that MANY games that inexplicably did not work for me in steam (crashes on startup) now work perfectly!
I am very please with this update, needless to say.

**NEW INSTRUCTIONS**
1. Remove old fglrx installation completely:
```
sudo apt-get remove --purge fglrx fglrx-dev fglrx-core fglrx-amdcccle
```

2. Reboot. You will have display back! Co-incidentally, you'll also have rudimentary 3d acceleration. That's right, the saga detailed below is no longer an issue. So, you can stop here if you don't need good acceleration.

3. Install the packages from the repos:
```
sudo apt-get install fglrx fglrx-core fglrx-dev fglrx-amdcccle
```
OR (if you want newer updates as they come)
```
sudo apt-get install fglrx-updates fglrx-updates-core fglrx-updates-dev fglrx-amdcccle-updates
```
(yes, the amdcccle package is named inconsistently, no idea why)

4. Initialise the configuration:
```
sudo aticonfig --initial
```

5. Reboot, you're done.



**ALL INFO FROM THIS POINT ON REDUNDANT** (but I'll leave it here for.... posterity I guess)
UPDATE -10/12/2014: AMD has just released an updated driver for linux (the "OMEGA" update). This means the below instructions may no longer be valid -  I will update the guide if necessary when I get time.
**UPDATE - 12/12/2014: **updating the guide to be current.
**IMPORTANT RED FLAG - **Right now these drivers are fundamentally incompatible with WINE and PlayonLinux due to the fglrx-core package. basically it replaces the libopencl packages which are a WINE dependancy. I think it is possible to get it working with some tinkering but it is beyond my powers. FAIR WARNING.

There seems to be a bit of interest in getting the r9200 series cards working in 14.04, so I thought I would write up a quick guide on how I got my r9270x working properly on my system.
Info is from a variety of sources, and some figured out on my own.


My GPU is an r9270X but these instructions *should* work for any r9200 series card.
I tried to be as detailed as possible so anyone can follow the procedure - this took me almost two weeks to get working but following this process you should be done in under an hour.
I hope that some other users can benefit from my suffering :D
Note also that the drivers are in fact in beta and are not perfect. Expect occasional bugs. Expect some games not to work (most notably for me, The Witcher 2).


**CURRENT as at 12/12/2014 - AMD OMEGA drivers version 14.12**


Hardware details -
**MOBO:** Z87-D3HP (off topic - this board needed a BIOS update to boot at all with the below CPU. Z97 would have worked out of the box)
**CPU:** i5-4690K
**RAM:** 8GB DDR3
**GPU:** R9270X 4GB
**SSD:** 1TB 840 EVO


**Software details -** 
Kubuntu 14.04.1, clean install, fully updated as at 12/12/2014
*Steam*


I'll assume people using this card are gamers and include Steam in this guide as it is a bit temperamental with detecting your hardware.
**UPDATE: Steam seems to require no special treatment now. Instructions for it remain only in case people have issues.**

PROCEDURE


**1. Don't install the card yet.**
**UPDATE - 12/12/2014: **I have tested with the new drivers and you still need to do steps 1 through 3 to get display working initially. Sucks. 

I recommend not installing the card and starting this process using your onboard motherboard graphics. Even with monitor plugged in to the motherboard, my bootloader was getting confused if the r9270x was installed. It is necessary to set the "nomodeset" parameter to stop grub from trying to set a graphics mode before lightdm starts (we'll cover that in a minute). 
If you have already installed the card then you can do steps 2 and 3 in recovery mode (press shift at boot to get the option) rather than removing it.


**2. BIOS/UEFI**
Go into your bios settings, and make sure that graphics is set to "VGA", instead of "Auto" or similar. This ensures that your virtual terminals will display properly after this process is completed. If you skip this step, Alt+F1 - F6 will likely just give you blank screens, making it very difficult to recover after a system crash.
Unfortunately I cannot give much more detailed instructions on this step as BIOS's vary so widely. refer to your manual if you can't find the option :)
Once that is done, move to step 2.


**3. nomodeset**
**NOTE: Only for recovery mode:** If you ARE in recovery mode, select the root command line option and remount root in read/write mode:
```
mount -o remount, rw /
```


From here the instructions are the same.
In a terminal (Alt+Ctrl+T, or just continue on if you are in the recovery mode console) and open your grub defaults file:
```
sudo nano /etc/default/grub
```


Find this line:
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**
And add nomodeset so it looks like this:
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"**


Ctrl+X to exit, and confirm you would like to save with "y".
Then:
```
sudo update-grub
```
Which will update your grub config to not try to detect a video mode.


Now reboot. If you did this from recovery mode you will need to shut your computer down as the updates don't stick until a proper reboot.
You should now have display from the graphics card! If it is not installed yet you can go ahead and drop the card in now.
But you won't have any hardware accelleration yet.


**Steam users:** If you use Steam, now's the time to install it. 
```
sudo apt-get install steam:i386
```
Run it, make sure you can log in.
Now exit steam completely and move on.


**4. Uninstall fglrx if you tried installing it already.**
**UPDATE 12/12/2014 - **no changes here. If you have fglrx installed you will need to remove completely. If you followed steps 1 through 3 you will have display without the drivers (albeit OpenGL will not work)

Open synaptic (or package manager of your choice) and mark all fglrx packages for complete removal. Command line method depends which version you installed and how - this guide assumes you may have tried either fglrx or fglrx-updates from the repos.
You'll also want to remove any residual configuration:
```
sudo nano /etc/X11/xorg.conf
```


If you get an error that the file does not exist - that's good. If you get a blank file - that's also good. If you get a file with "stuff" in it, delete all the contents and Ctrl+X to exit - confirm to save with "y".
If you have already done manual fiddling with xorg.conf then please save your custom options (e.g. for certain input devices) to a text file somewhere else so you can put them back later.
Reboot if you like (not strictly necessary).


[B]5. Get hold of the latest [s]beta[/s] drivers
UPDATE 12/12/2014:[/B] Beta drivers no longer neccessary (yay!). The OMEGA drivers from the AMD site work fine. Thet work in exactly the same way so the below instructions still apply.
Download the latest [s]beta[/s] linux drivers from AMD's website (amd.com). It will be a .zip file so extract it somewhere (I'll assume the standard downloads folder).
In your downloads folder you will now have a folder called "fglrx-14.20". Open a terminal and navigate to that directory:
```
cd ~/Downloads/fglrx-14.20
```
And run the AMD software:
```
./amd-driver-installer-14.20-x86.x86_64.run
```
**WARNING: Do not install using the AMD software.**
Instead, select the option to generate distribution specific packages. Select Ubuntu from the list and click next. The first time it will fail, click to see the error log. It will list the packages you need to install. 
Install the missing packages in the order they are listed using:
```
sudo apt-get install *packagename*
```
Once that is done, run the installer again, and select the same options as last time. This time it will work. You may not be able to see progress, but it is working, let it run.
Once that is done you will have three new files in the fglrx-14.12 directory - these are the packages we will install.


**6. Install the AMD packages (and other bits and bobs)**
**UPDATE- 12/12/2014: **The new drivers have an additional package fglrx-core, for some reason this package conflicts with a wine dependancy!! This should be a red flag right now. you WILL NOT be able to run wine on a system with the amd OMEGA drivers installed without some weird tinkering that is beyond my abilities. There is a guide somewher but I have not tried it. TBH I don't use WINE that much as there is so much Steam stuff working now.
I had to uninstall the following to get the "core" package to install:
Wine
PlayonLinux
LibOpenCL (both 32 and 64 bit packages)
My understanding is that fglrx-core provides an equivalent for libopnecl packages and wine will need to be updated so it can use it.....

You now have [s]three[/s] four .deb packages - fglrx-core, fglrx, fglrx-ccc, and fglrx-dev. The file names will include version numbers as well so note down the full file names.
Assuming you are in the command line you can just list the contents of the folder for easy copying:
```
cd ~/Downloads/fglrx-14.20
ls
```
 Install them like so (substituting the file names for your actual generated package names):
```
cd ~/Downloads/fglrx-14.20
sudo dpkg -i fglrx-core-*version*.deb fglrx-*version*.deb fglrx-dev-*version*.deb fglrx-ccc-[i]version[/].deb
```
**DO NOT REBOOT YET!**


Now you want to generate a fresh xorg.conf file:
```
sudo aticonfig --initial
```
This will back up your current xorg.conf (as "xorg.conf-original") and create a shiny new one.
If you had important customizations in there then go now into the file and add them back:
```
sudo nano /etc/X11/xorg.conf
```


**IMPORTANT:** If you use Steam, run it *right now*. This is important - if you do not do this it will refuse to recognize the video card after rebooting and you'll need to start again from step 3. This is most likely a bug with steam.


Having done that, you'll also want to install the following packages. These are the proper names for the ones listed in the 14.6 beta notes on the amd site, and I only found them from step 4 of this guide on the ubuntu wiki:
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)
So - thankyou wiki :)


```
sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
```


**7. The last throes**
You would think we were done but no, there's one last step. 
**UPDATE - 12/12/2014**: This was not necessary with the OMEGA (4.12) drivers. the xorg.conf file survived reboot without being renamed and worked fine. In KDE I did need to go into desktop effects settings and set it back to OpenGL to get effects fully functional. I'll leave this here though in case it happens still for others.

Reboot your system now and **when it starts back up you may or may not have display.** If it broke completely then you'll need to go into recovery mode (pressing shift key at boot time).


If you're in recovery mode drop into root console and remount the root directory in read/write mode:
```
mount -o remount, rw /
```
The rest is same whether you are in recovery mode or not.


For some unknown reason, the system has decided that it should rename your xorg.conf file instead of copying it and renaming the copy. This causes the system to auto-detect which is busted on this card. So go into your X11 folder and find out what it is called:
```
cd /etc/X11
ls
```
"ls" will list the contents of the folder. Look for xorg.conf. YOu should have at least two of them, an xorg.conf-original which is your old one (if you had one) and xorg.conf-mmddyyyy where "mmddyyyy" is today's date.
Then open that file:
```
sudo nano xorg.conf-mmddyyyy
```
Press Ctrl+O to save, and ensure to rename to plain old "xorg.config" (without quotes).
Press Ctrl+X to exit nano.
Reboot.


Once again, if this was done in recovery mode, you may need to shut down completely for things to stick.


**Congratulations!**
You made it. You now have a working r9200 series card on ubuntu 14.04.
You may want to open Catalyst Control Centre (it will be searchable in your applications menu (dash, k menu, or whatever) and turn on anti-tearing in the options. The driver is not optimised and tearing/artifacting can be an issue.

---

### Post by mörgæs on 2014-09-18
Thanks for the guide. If you mark it solved using "thread tools" there's a better chance that someone finds it.

---

### Post by maxinstuff2 on 2014-09-18
> **mörgæs said:**
> Thanks for the guide. If you mark it solved using "thread tools" there's a better chance that someone finds it.
Done!

---

### Post by waffleguy4 on 2014-09-25
wow that is a long ordeal to get a silly card fixed. but thanks for the documentation a ton!

i think this described my problem - i have a AMD Radeon R9 280X 3 GB - and OpenGL, hardware acceleration, etc doesn't work correctly. does that sound right?

do you think this will ever be fixed in ubuntu, or is my card just bad? it came with a desktop i bought on newegg...

thanks!

---

### Post by tutenstain2 on 2014-09-25
Thanks but I am having problem on the part where you have to rename the xorg.config. I rename it and reboot and I still have a black screen. Then I see that once rebooted it seems that it have not been saved as xorg.conf as it has been overwritten.

---

### Post by maxinstuff2 on 2014-10-08
> **waffleguy4 said:**
> wow that is a long ordeal to get a silly card fixed. but thanks for the documentation a ton!

i think this described my problem - i have a AMD Radeon R9 280X 3 GB - and OpenGL, hardware acceleration, etc doesn't work correctly. does that sound right?

do you think this will ever be fixed in ubuntu, or is my card just bad? it came with a desktop i bought on newegg...

thanks!

Yes I have tested and 3d acceleration does not work without the beta drivers, you may have an easier time than above given you actually have display already :) the process to install the drivers themselves should work as described above.

---

### Post by maxinstuff2 on 2014-10-08
> **tutenstain2 said:**
> Thanks but I am having problem on the part where you have to rename the xorg.config. I rename it and reboot and I still have a black screen. Then I see that once rebooted it seems that it have not been saved as xorg.conf as it has been overwritten.
Yes for some reason the system (not sure if kernel or the driver software is responsible) renames it to xorg.conf.*thedate*.
you need to find it and rename it back to the right name and reboot again.

---

### Post by maxinstuff2 on 2014-12-12
Updated the guide to be current with the new drivers from AMD.

THis is an important update as WINE compatibility is broken due to some dependancy silliness. I have no idea how to get it working. 

Honestly I don't use WINE much anymore so have just uninstalled it (and libopencl, the conflicting dependancy) for now.

---

### Post by Yellow Pasque on 2014-12-12
Heh, when I read the title I thought it was about the old Radeon 9200.

---

### Post by Joe_Thorpe on 2015-04-14
Hi, sorry to revive an old thread, but i've been following this guide with my XFX R9 280X,  and have followed all steps up to running the installer to get the packages. I ran ./amd-driver-installer-14.501.1003-x86.x86_64.run and got errors. So i installed the packages as mentioned (however this error was not shown within the AMD software, but in a gnome window). So i installed the packages, proceeded through again but got more errors.

I can't make sense of /usr/share/ati/fglrx-install.log maybe someone here will know what i've done wrong?

[https://docs.google.com/document/d/1WWdrmFxegh9LUfbqm8coqJuYGq4XXvwKLQQl90B-BTY/edit?usp=sharing](https://docs.google.com/document/d/1WWdrmFxegh9LUfbqm8coqJuYGq4XXvwKLQQl90B-BTY/edit?usp=sharing)

---

### Post by Yellow Pasque on 2015-04-14
^You don't have the prerequisite packages installed: [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Before_you_start](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Before_you_start)

---

### Post by Joe_Thorpe on 2015-04-14
> **Temüjin said:**
> ^You don't have the prerequisite packages installed: [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Before_you_start](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Before_you_start)


Thank you for sharing that link.

I used a work around to avoid the issue with the drivers and LTS Enablement on 14.04.2 however, the package, "xvba-va-driver 0.7.8-1ubuntu3" didn't install. I believe that package is related to hardware acceleration, so that's rather important.

I tried to install it once, and got an error. Unfortunately i didn't get a chance to write it down. After a reboot i get "couldn't find any package xvba-va-driver 0.7.8-1ubuntu3"

I had steam installed as per the OPs guide, but somehow it was uninstalled during the process. Reinstalling it worked ok.

I really don't know what to do here...

---

