---
title: "How To: Install Intel® 945GM x86/MMX/SSE2 graphics Ubuntu 12.04"
date: 2012-10-17
forum: Hardware
---

### Post by pitviper296 on 2012-10-17
This is going to be my first how to guide: Installing Intel 945GM x86/MMX/SSE2 graphics Driver in Ubuntu 12.04 LTS. These steps worked for me on my machine and I was able to replicate the steps and outcome in a vmware virtual machine on WinXP as well. 
  
 Before you begin I must say you will need to install a PPA to get this driver to be recognized in Ubuntu. A PPA is (Personal Package Archive)  
 The package we will be installing can be found here **[COLOR=Red][https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) [/COLOR]**
  
 [COLOR=Red]****Important: **[/COLOR]The contents of Personal Package Archives are not checked or monitored. You install software from them at your own risk. - From Launchpad 
 I will assume no responsibility for any harm to your computer as a result of following this guide, nor may I be of much help if these steps cause harm to your computer or if they fail to work. 
  
 Before we begin lets verify that your driver is not correctly configured in Ubuntu. You can do this by clicking: System Settings - Details - Graphics. 
 If Ubuntu is using the correct driver you should see: Driver Intel® 945GM x86/MMX/SSE2 , Experience: Standard. If not, continue with the following steps.
After careful thought I have decided that it may be possible to skip to step four. I seem to remember step 3 being already installed in Ubuntu, but I'm not positive. If it was already installed adding the xorg.conf file to etc/X11 directory and rebooting may solve your problem. If you wish to try it first please post your outcome.  
  
 All steps will be carried out from a terminal. Fell free to copy and past commands to complete the process. 

[COLOR=Red]**[COLOR=Black] Edit:[/COLOR]** ** After doing some reading and trying to fix the same problem on a Toshiba Satellite L500 I realized that you will also need. mesa-utils **[/COLOR]

sudo apt-get install mesa-utils 

  
 Step 1: Open a terminal session by pressing CTRL+ALT+T 
  
 Step 2: Enter command " sudo add-apt-repository ppa:ubuntu-x-swat/x-updates " Installs the nessary PPA to your system 
  
 Step 3: Enter command " sudo apt-get install xserver-xorg-video-intel " This installs the drivers for you graphics chip 
  
 * Ubuntu no longer uses xorg.config file. You will have to create this file in the next step and enter in values. 
  
 Step 4: Enter Command " sudo gedit /etc/X11/xorg.conf " This command will create the file and open it for you. Insert the text below exactly as it appears and click save. 
  
 Section "Device" 
  Identifier "Card0" 
  Driver "intel" 
  Option "AccelMethod" "sna" 
 EndSection 
  
  
 * Last step , restart your interface or just reboot you machine and go back to system settings - details - graphics and verify that your drivers are displayed. Best of luck and if you have any questions I'll try my best to help. * 
  
 P.S A special thanks to the guys at #Ubuntu IRC channel for all their help and time and support, I'd also like to thank yigal and BlueEagle from the channel for helping me sort out my xorg.conf questions.

---

