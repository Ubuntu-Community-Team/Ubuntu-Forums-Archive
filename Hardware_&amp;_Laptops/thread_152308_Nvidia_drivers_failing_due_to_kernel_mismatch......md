---
title: "Nvidia drivers failing due to kernel mismatch.....anyone help?"
date: 2006-03-29
forum: Hardware &amp; Laptops
---

### Post by gordong11 on 2006-03-29
Hi 

I'm using-64 bit Breezy an a newly built system. My Motherboard is a gigabyte -GA-K8n51GMF socket 754, with onboard Nvidia 6100 graphics and ALC850 (AC97) sound.

I have been trying to install both the latest drivers for graphics and the forceware sound, but have had no luck at all. One issue after another. I just re-installed the OS for 4th time.

I'm getting kernel errors when I try and run the latest drivers, and forced to abort. IE 3.4 but have 4.0 or something like that. I have tries to follow the directions for methods 1 and 2. Method 1 definitely is not going to work. Method 2 seems like it may, but I must be doing something wrong.

Currently I have my PC set to VESA, but does not solve my no sound issue. Breezy is even recognizing my sound device, hence needing the Nvidia Forceware.

**Can someone point me the latest post for installing the downloaded Nvidia8178 drivers**? there are like 3. Also if nned be is there is an expert out there I can offer to pay for phone support to get this thing running good. Hope thats not taboo here, but I'm frusterated.

Right now, I have a fresh 64 bit 5.10 install, only updates and multiverse enabled...in VESA mode. Thanks for the help.

Gord

---

### Post by Sutekh on 2006-04-01
-Is this the link you have tried?

[Ubuntu Forums - HOWTO Latest NVIDIA Drivers](http://ubuntuforums.org/showthread.php?t=75074)

 - Method 1 will only install the **7667** drivers, Method 2 will install the **8178** drivers.

 - Can you run through the commands and when you encounter problems make good notes of the errors.  Post them here, I'm sure we can help with this.  I have installed the NVIDIA drivers many times with this method and you should be fine if you follow the instructions to the letter.

 - From what you've said it sounds like the official NVIDIA Installer fails when it **compiles the kernel module**?  The problem (and a rather silly one) is that the kernel was compiled with the GNU C compiler v3.4 (gcc-3.4) but when you install the compiling tools package (build-essential), version 4.0 gcc-4.0 is installed. 

 - Thus this important step in the process

```
cd “directory where you have the nvidia installer”
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
```
 - This forces the installer to use the GCC v3.4 to compile the NVIDIA driver, so it can be included in the kernel and get your video working.

 - Try Method 2 again and lets us know how it goes.

---

### Post by gordong11 on 2006-04-01
I'm having a couple of issues with 2 of the steps here:

[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=latest+nvidia](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=latest+nvidia)


Step 7;
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common

This working OK. but then....

[B]Step 8

admin@ubuntu:~$ sudo rm /etc/init.d/nvidia-*
rm: cannot remove `/etc/init.d/nvidia-*': No such file or directory

Step 10: after stop GDM

and maybe I'm putting this in wrong? I'm pressing enter after each line. For example: cd ~/Desktop/ then enter, su then enter, CC=gcc-3.4 then enter...etc

or is there another way to do this code?

cd ~/Desktop/
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC[/B]

Do I need to do both step 7 and 8? Step 10: should be pressing enter after achline of code? If not how do I enter this?

Thanks for the help!!

Gord :???:

---

### Post by Sutekh on 2006-04-01
[QUOTE=gordong11]
Step 8

admin@ubuntu:~$ sudo rm /etc/init.d/nvidia-*
rm: cannot remove `/etc/init.d/nvidia-*': No such file or directory
[/QUOTE][B] - That's cool this happens to me.  It simply means that there was no file to delete.  This step was put in just in case there was a startup script for the NVIDIA drivers.  That's not a problem.  (Sorry for the bold, I couldn't remove it :()

[QUOTE=gordong11]
Step 10: after stop GDM

and maybe I'm putting this in wrong? I'm pressing enter after each line. For example: cd ~/Desktop/ then enter, su then enter, CC=gcc-3.4 then enter...etc

or is there another way to do this code?

cd ~/Desktop/
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC[/B]

Do I need to do both step 7 and 8? Step 10: should be pressing enter after achline of code? If not how do I enter this?

Thanks for the help!!

Gord :???:[/QUOTE]
 - Yes enter each line then press enter.  You can put more than one command together on a line by using &&.  So like
```
su
CC=gcc-3.4 && export CC && exit
CC=gcc-3.4 && export CC
```
 - But I wouldn't bother just enter them in one at a time.  You won't get any sort of return from the command line, just keep going.  


 - You are almost there, the next step is to run the NVIDIA installer.  


 - If its the **v8178 drivers** then you don't need to do the editing of xorg.conf just go straight to step 12 to restart the display manager.


 - When you get to step 13, which creates a menu entry for the NVIDIA settings, just make sure that there isn't one already in the Applications -> System Tools menu.

---

