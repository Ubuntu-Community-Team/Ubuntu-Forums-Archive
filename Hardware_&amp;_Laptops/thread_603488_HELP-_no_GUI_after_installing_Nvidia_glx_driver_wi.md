---
title: "HELP- no GUI after installing Nvidia glx driver with adept"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by balaknair on 2007-11-05
I just installed nVidia glx drivers(new) using adept on Kubuntu 7.04, after reboot I don't get the log on screen, just a black screen with a blinking cursor. I checked some of the other posts here about similar issues, but I can't make head or tail of most of the suggested solutions. I'm a total newbie at this.

---

### Post by balaknair on 2007-11-05
OK
I was getting just a black screen with a blinking cursor
 tried this:

hit alt+F1
log in

"sudo dpkg-reconfigure xserver-xorg"
set driver to vesa

typed "startx"

now the x GUI starts up, though can't get the full resolution supported by my monitor.

---

### Post by aoanla on 2007-11-05
More information please! What graphics card do you have? Are you running 32 or 64bit Ubuntu? 
Can you reproduce the issue, and then get a copy of your /var/log/xorg.0.log for us? (Logging in in recovery mode after a crash should retain your old xorg.0.log without overwriting it, so copy it elsewhere before rebooting and then fixing your problem again.)

---

### Post by Tanker Bob on 2007-11-05
I only ever install the nvidia drivers with the envy script [here](http://albertomilone.com/nvidia_scripts1.html). Any other method is shooting in the dark. You will need to uninstall the drivers that you installed through adept before running the script.

---

### Post by balaknair on 2007-11-05
I'm using Kubuntu 7.04 32-bit version, Kernel 2.6.20.16.28.1


tried using envy as you said just now, got this error

"python pulse.py nvidia 
root@Bala-LinuxK:/usr/share/envy# python pulse.py nvidia 
Envy - Version 0.9.8
Ubuntu Feisty 32bit
Your graphic card has been detected as a GeForce 8400 GS
Your graphic card is supported by the latest driver
OK: All the packages are installed
Checking the Dependencies for the New Method
ENVY: The following packages are not installed:
kernel-wedge
sharutils
libgtk2.0-dev

ENVY: attempting to install the packages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtext-glob-perl libdate-calc-perl m4 metacity-common libcarp-clan-perl
  libgnome-menu2 dcraw libpanel-applet2-0 libgnome-window-settings1
  libmetacity0 libfile-find-rule-perl libgnome-desktop-2
  libnumber-compare-perl libbit-vector-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libatk1.0-dev libcairo2-dev libglib2.0-dev libpango1.0-dev
Suggested packages:
  libcairo2-doc libglib2.0-doc libgtk2.0-doc libpango1.0-doc mailx
The following NEW packages will be installed:
  kernel-wedge libatk1.0-dev libcairo2-dev libglib2.0-dev libgtk2.0-dev
  libpango1.0-dev sharutils
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 4251kB of archives.
After unpacking 15.2MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  kernel-wedge libglib2.0-dev libatk1.0-dev libcairo2-dev libpango1.0-dev
  libgtk2.0-dev sharutils
E: There are problems and -y was used without --force-yes
ENVY ERROR: The following packages cannot be installed:
kernel-wedge
sharutils
libgtk2.0-dev"

---

### Post by Tanker Bob on 2007-11-06
Hmmm. Did you try to install those packages yourself and then running envy?

---

### Post by FooAtari on 2007-11-06
Im having issues with the Nvidia drivers.

does Envy use the same driver as the installing them via the Restricted/Proprietary drivers menu? Is it the most up to date driver?

Thanks

---

### Post by balaknair on 2007-11-07
First I tried using adept, GUI failed on reboot, then after trying dpkg-reconfigure and getting the GUI back, I tried uninstalling the nvidia driver, and then installed envy

---

### Post by balaknair on 2007-11-07
so far I've checked out quite a few of the guides on ubuntuforums, and tried most of the instructions given, and it's always the same result- GUI crashes on restarting X.
Maybe I'm doing something wrong, I'm not sure.
Thanks for all your help and advice. I think I'll get back to trying to figuring this one out after the 10th, got a lot of backlogs to clear at work till then.

---

### Post by Tanker Bob on 2007-11-07
Are you sure that the 8400 card is supported by the driver?

---

### Post by balaknair on 2007-11-09
@tanker bob
When I tried installing with envy, it says the card is supported, though it isn't listed in the supported cards list ([http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html))

I also checked the nvidia site, I think I'll try installing the official linux driver they provide after I get home after work tomorrow.
Will let you know how it goes.
Thanks for all your help, I'm very grateful.
I really think the Ubuntu community is one of the best things about the Ubuntu experience.
Thanks

---

### Post by Tanker Bob on 2007-11-09
If it isn't listed in the appendix as a supported card, it doesn't look good. In the NVidia Linux forum, NVidia says they are working on support for the latest cards but as of a week ago it wasn't available yet.

---

