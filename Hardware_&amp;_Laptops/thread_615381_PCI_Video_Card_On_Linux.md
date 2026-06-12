---
title: "PCI Video Card On Linux"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by echolink on 2007-11-17
**How to Install a Nvidia/ATI PCI Video Card on Linux**


	Hello my name is echolink, and the PCI Nvidia/ATI video card, issue seems to be a plague for a lot of Linux, or aspiring Linux users, and has actually been one reason that a lot of users, have dismissed Linux, because of this one issue. Simply due to the fact that they cant use there video card. I don't blame them who wants to use on board video when you have a perfectly good Nvidia/ATI PCI card laying around. Thats why I have decided to write this simple how to article for people in hopes that it will open up more users to the world of Linux. I have found it to be somewhat sad that people wont use Linux because of a simple hardware issue that has not been corrected as a default action by many Linux Distribution Developers and Companies. So go ahead and proceed below and we will get your video card up and running. :)



	Before you proceed ask yourself a question have you ever wanted to use Linux, but are stuck with a pci only motherboard with a pci card, and there is no option in the bios to disable the damn on board video card. Well I have a surprise for you there is a simple easy way to do this **provided you follow the instructions below!!!!!**. To do this however you need to understand why the pci video card does not automatically detect as default on most Linux distros, when windows, or other operating systems will. Well thats simple the Linux system is going to detect the closest default motherboard video chip set regardless of what you bios is set on because most Linux distributions overlook the bios and detect all the hardware that is on the machine regardless if you have something disabled in the bios this all has to do with PCI bus issues. Lets just say Linux is a very intuitive operating system far superior to windows. So the fact that the Linux distribution you have chosen detects the hardware is a good thing because we all know that Linux is picky when it comes to hardware detection. The reason that AGP, and PCIe do not have this issue is because they are not on a PCI bus system, they are on a different bus, to were PCI cards, and On Board cards are on the same PCI bus system, but we will discuss more about this later in the article. So lets go ahead and set up your PCI video card so you can get the performance you expect instead of using the crappy on board video driver that the motherboard manufacture provided with the motherboard.

Step 1

	First off all install the operating system on the on board video card this will save hassles later on.

Step 2 

	Okay no that we have the Linux distro of your choice installed, and you are now booted up on clean fresh install. Go ahead and open up the terminal/konsole (some distro's call it different things), Ohhh NO did you say TERMINAL!! :) now before you get scared this is actually easy :) go ahead and log on under root, by first typing **su** now it will ask you for your password that you provided as the root password during the installation. so go ahead and enter your **password**. Now that you have done this go ahead and copy and paste, or type the following command **sudo dpkg-reconfigure xserver-xorg**. Now that we have completed this step go onto step 3.

Step 3

	Okay now that we have started the xserver-xorg configuration tool, the next few steps will be fairly easy. Basically all you need to do is answer the following questions that the system asks you Type of video card, PCI bus, keyboard, mouse, monitor, etc. **IMPORTANT: MAKE SURE YOU READ EVERTHING BEFORE YOU JUST START DEFAULTING ON STUFF!!!!!!! IF YOU DO IT WRONG YOU HAVE TO START OVER, BUT THIS TIME IN TEXT MODE OF THE OPERATING SYSTEM!!!**.  The one thing that you need to pay particular interest to is the PCI bus number, because by default if you are running a pci only mobo, the xserver-xconfig tool will detect the pci bus for the on board video card not your Nvidia/ATI card. **This is the Ghost Problem That Cause PCI Cards Not To WORK THAT WAS MENTIONED AT THE BEGINING, And Is Why PCI Cards Dont Work By Default!!!!** So we need to find out what bus the Nvidia/ATI card runs on. So we need to look into your hardware manager to find you what the bus is. **So go ahead and MINIMZE (Not Close)**, your terminal to the task bar. Go ahead and navigate to were ever your hardware manager is located on your particular distribution. Once you are inside of your hardware management area you need to locate the Nvidia/ATI video card and look at the bus, the bus will read like this for example: **bus:1:9:0 (which is default for most motherboards, the on board is usually bus:0:2:0, but make sure just to be safe what yours is)**. Okay now that you have your bus ID go ahead and bring back up your terminal and enter the bus ID into the xserver-config tool. Once you answer this go ahead and answer the rest of the questions . Now that you have correctly set up your xconfig file and saved it. You can close the terminal and you can reboot the system. When your computer brings up the settings screen at the beginning of reboot go into bios and set your video to pci, and plug the moniter into the video card, again reboot, and bam you have a working PCI ATI, Nvidia video card. After you complete these steps follow the proper procedures, related to your specific distribution and install the nvidia/ati drivers, after installing the drivers, you need to reboot, and your Nvidia/ATI installation will be complete. You can go into the nvidia control panel and adjust settings for things like dual monitors, etc later. 

So in closing I hoped this little tip helps a lot of you frustrated Linux users who want that PCI card to work but just cant seem to get it going. This is echolink saying see you later. And happy Linux......

---

