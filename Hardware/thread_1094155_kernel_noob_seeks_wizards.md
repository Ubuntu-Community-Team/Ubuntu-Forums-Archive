---
title: "kernel noob seeks wizards"
date: 2009-03-12
forum: Hardware
---

### Post by anthonie on 2009-03-12
Hi all,

I own an ASUS X50GL/F5G dualcore laptop

I initially had 8.04 installed and upgraded from that to 8.10. Both 64 bit ofcourse. 

Nice little machine and generally speaking, Ubuntu runs great on it, with a few exceptions.
My battery status and the like, are not functioning, due to a dsdt problem. Now the strange thing is that when I use the 8.04 live CD, battery status and hence, the powerdown actually work flawlessly. In short, I seem to have problems with the general acpi functionality of this machine. So, that got me thinking of a kernel recompilation. I know I could wait for the new Ubuntu version, coming out next month, but I'd rather take the learning path and deal with the problem myself (that is, with the help of people in the know).

The problem I have is that I do not know what to look for, the modules that need recompilation. I've got plenty of documentation on recompiling a kernel, but the exact module, or the way to find out what it is exactly, that needs to be recompiled, with that I'm in the dark.

Is there any difference between compiling 32bits versus 64bits? Culprits I need to be aware off? Other questions I can't even think off but that need to be asked anyway?

So, are there any kernel wizards out here that would be willing to spend a little time on an eager to learn user and point him in the right direction?

regards,

Anthonie

---

### Post by eeperson on 2009-03-23
I am guessing that the problem you are having is not due to the configuration of your kernel(although I could be wrong).  I am guessing that it is due to a regression in the version of the kernel you are running. That being said, compiling a new kernel might fix your problem.

There are several ways to compile a kernel.  You can find several Debian/Ubuntu specific methods for compiling a kernel [here]("https://help.ubuntu.com/community/Kernel/Compile").  These are probably much fancier than you need as they produce .deb packages.

So, I will give you probably the easiest way to compile and configure a new kernel. I am assuming that you are fairly familiar with Ubuntu.  These instructions are Debian/Ubuntu specific.

I recommend trying this out on a machine you don't care about or in a virtual machine first.  This process can damage you existing install if you make certain mistakes.  Backup everything before attempting this on a machine you care about.
 
1. Download a copy of the source code for the kernel version you want to compile.  Extract it to a directory in your home folder somewhere if necessary.
 
2. Install the packages 'build-essential' and 'ncurses-dev'.  The first package is required to compile the kernel the second is used required to configure the kernel before you build it.

3. Go to the /boot directory and copy the the config file from your current kernel.  This file will be called something like config-2.6.27-11-generic.  The name will differ slightly but it will contain the version number of your current kernel.  Paste it in the folder that contains your kernel source code.  This file contains the configuration that was used to generate you existing kernel.

4. Configure your new kernel.  To do this open a terminal and navigate to folder containing the new kernel source code. Then type: 
```
make menuconfig
```
This will start a text based tool to configure your kernel.  There are other tools configure your kernel but this one is the most basic.  Navigate down to the bottom of the menu and select the option that is something like 'load existing configuration'.  Then type in the name of the config file that you just copied.

Now you just navigate through the menus and configure the kernel how you want.  If you poke around long enough you should be able to find ACPI related sections.  When you are done just exit the menu and it will ask you if you want to save your configuration.  Save it.

5. Build your kernel.  Now (from the folder containing the source code) type the following commands:
```
make
sudo make install
sudo make modules_install
```
The first line will build the kernel(which will probably take awhile).  The second line installs the kernel and the third line installs the loadable modules related to the kernel.

6. Update boot related files.  First type this command in the terminal with the *your kernel version here* part replaced with the version number of the kernel you just compiled:
```
sudo update-initramfs -c -k *your kernel version here*
```
This generates a file that is needed for Linux to boot.

Then enter the command:
```
sudo update-grub
```
This updates your boot menu to include the new kernel.


That is it, just reboot your computer and you should boot to the new kernel.  Hopefully this will get you started.

---

