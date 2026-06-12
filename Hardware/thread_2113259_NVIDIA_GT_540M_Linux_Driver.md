---
title: "NVIDIA GT 540M Linux Driver"
date: 2013-02-06
forum: Hardware
---

### Post by MartianTek3 on 2013-02-06
Hello Everyone, 

This post is for people who have sufficient knowledge with handling Nvidia graphics drivers installations 

Particularly with the GT 540M on a Kubuntu 12.10 (64 bit)

I will explain what I did: 
1. Went to the Nvidia Website ---> [http://www.nvidia.com/object/linux-display-amd64-310.32-driver.html](http://www.nvidia.com/object/linux-display-amd64-310.32-driver.html)

2. I downloaded NVIDIA-Linux-x86_64-310.32.run

3. I know I need to shutdown the X server and Nouveau (the reverse engineered nvidia replacement) in order to run the installer

4. [http://us.download.nvidia.com/XFree86/Linux-x86_64/310.32/README/commonproblems.html#nouveau](http://us.download.nvidia.com/XFree86/Linux-x86_64/310.32/README/commonproblems.html#nouveau)
(an excerpt)
	
[I]What is Nouveau, and why do I need to disable it?

A simple way to prevent Nouveau from loading and performing a kernel modeset is to add configuration directives for the module loader to a file in /etc/modprobe.d/. These configuration directives can technically be added to any file in /etc/modprobe.d/, but many of the existing files in that directory are provided and maintained by your distributor, which may from time to time provide updated configuration files which could conflict with your changes. Therefore, it is recommended to create a new file, for example, /etc/modprobe.d/disable-nouveau.conf, rather than editing one of the existing files, such as the popular /etc/modprobe.d/blacklist.conf. Note that some module loaders will only look for configuration directives in files whose names end with .conf, so if you are creating a new file, make sure its name ends with .conf.

[COLOR="blue"]Whether you choose to create a new file or edit an existing one, the following two lines will need to be added:

blacklist nouveau
options nouveau modeset=0[/COLOR]

The first line will prevent Nouveau's kernel module from loading automatically at boot. It will not prevent manual loading of the module, and it will not prevent the X server from loading the kernel module; see "How do I prevent the X server from loading Nouveau?" below. The second line will prevent Nouveau from doing a kernel modeset. Without the kernel modeset, it is possible to unload Nouveau's kernel module, in the event that it is accidentally or intentionally loaded."[/I]

5. Bear with me, i have to write a new file /etc/modprobe.d/
The PROBLEM is that the directory is write-protected.

6. How can i copy  "disable-nouveau.conf" to  /etc/modprobe.d/

7. My goal is to remove Nouveau and use Nvidia's driver

8. ](*,) Now I await further instruction

---

### Post by phthano on 2013-02-07
> **MartianTek3 said:**
> Hello Everyone, 

This post is for people who have sufficient knowledge with handling Nvidia graphics drivers installations 

Particularly with the GT 540M on a Kubuntu 12.10 (64 bit)

I will explain what I did: 
1. Went to the Nvidia Website ---> [http://www.nvidia.com/object/linux-display-amd64-310.32-driver.html](http://www.nvidia.com/object/linux-display-amd64-310.32-driver.html)

2. I downloaded NVIDIA-Linux-x86_64-310.32.run

3. I know I need to shutdown the X server and Nouveau (the reverse engineered nvidia replacement) in order to run the installer

4. [http://us.download.nvidia.com/XFree86/Linux-x86_64/310.32/README/commonproblems.html#nouveau](http://us.download.nvidia.com/XFree86/Linux-x86_64/310.32/README/commonproblems.html#nouveau)
(an excerpt)
	
[I]What is Nouveau, and why do I need to disable it?

A simple way to prevent Nouveau from loading and performing a kernel modeset is to add configuration directives for the module loader to a file in /etc/modprobe.d/. These configuration directives can technically be added to any file in /etc/modprobe.d/, but many of the existing files in that directory are provided and maintained by your distributor, which may from time to time provide updated configuration files which could conflict with your changes. Therefore, it is recommended to create a new file, for example, /etc/modprobe.d/disable-nouveau.conf, rather than editing one of the existing files, such as the popular /etc/modprobe.d/blacklist.conf. Note that some module loaders will only look for configuration directives in files whose names end with .conf, so if you are creating a new file, make sure its name ends with .conf.

[COLOR="blue"]Whether you choose to create a new file or edit an existing one, the following two lines will need to be added:

blacklist nouveau
options nouveau modeset=0[/COLOR]

The first line will prevent Nouveau's kernel module from loading automatically at boot. It will not prevent manual loading of the module, and it will not prevent the X server from loading the kernel module; see "How do I prevent the X server from loading Nouveau?" below. The second line will prevent Nouveau from doing a kernel modeset. Without the kernel modeset, it is possible to unload Nouveau's kernel module, in the event that it is accidentally or intentionally loaded."[/I]

5. Bear with me, i have to write a new file /etc/modprobe.d/
The PROBLEM is that the directory is write-protected.

6. How can i copy  "disable-nouveau.conf" to  /etc/modprobe.d/

7. My goal is to remove Nouveau and use Nvidia's driver

8. ](*,) Now I await further instruction

In the terminal type:

```
sudo kate /etc/modprobe.d/disable-nouveau.conf
```

This will open the Kubuntu text editor with superuser privileges.
Add whatever text you want and save it.

---

### Post by n00ne on 2013-02-07
I did the following steps yesterday on 12.10 64bit
with Nvidia 520GT and it worked for me but only on ubuntu
(I tried on cubuntu as well but I could not get ride from the nouveau error so I hope it will work with kubuntu)->

download nvidia binary form there website

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential linux-headers-$(uname -r)
sudo apt-get remove --purge nvidia*
sudo apt-get remove --purge xserver-xorg-video-nouveau

```


In the vim / gedit or any other text editor, I added the following lines to /etc/modprobe.d/blacklist.conf :
```

blacklist amd76x_edac 
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

```

restart !

go to tty1 or any other terminal (not in x) and stop x
```

sudo service lightdm stop 

```

now run nvidia driver as root (sudo Nvidia-bla-bla...)
and follow the instructions (I clicked yes on every option including chage my xorg setting).

I hope is some one can explain to me how can I make the driver to recompile on kernel update. I just had an update to day and had to manually download the new kernel headers and run the nvidia driver again. the thing is its a bunch of computers we use at work and I don't want to go and manually install the drivers again on every kernel update.

---

### Post by MartianTek3 on 2013-02-08
n00ne, 
I followed your instructions to the letter (maybe not)

1.I did 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential linux-headers-$(uname -r)
sudo apt-get remove --purge nvidia*
sudo apt-get remove --purge xserver-xorg-video-nouveau

2.Then i gave superuser privileges to Kate in order to edit the blacklist.conf 

While editing the configuration file should i erase everything in it and paste the: 
blacklist amd76x_edac 
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv 

3.I restarted and went into tty1 (Crtl-Alt-F1)stopped lightdm

4. Navigated to the ~/Downloads 
5. sudo sh NVIDIA-Linux-x86_64.310.run 
6. It asks something like it will try to modifiy the xorg settings i click yes

7. This where I got stumped... It told me that some how the nouveau driver was still running (even after i uninstalled it :( ) 

8. Now my laptop is abit messed up due to this, Now i try to edit 
the blacklist file but its gone wacky no can do 

9. Waiting for more instruction :shock::idea:

---

### Post by Yellow Pasque on 2013-02-08
So the question is: Do you have an Optimus system with both an nvidia and intel GPU?:
```
lspci | grep VGA
```

---

### Post by MartianTek3 on 2013-02-09
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 [COLOR="RoyalBlue"]VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)[/COLOR]
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
09:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
0b:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
``` 

No I believe i do not have an Optimus setup only NVIDIA GPU 

* edit Wait! i do have it hmm

---

### Post by n00ne on 2013-02-09
Try to disable the built in gpu in the BIOS.

but I think you will still need to find a way to get ride
of the nouveau driver.
I don't know why this proccess fail to disable it properly but it's sounds like the same problem I had with cubuntu. in the end I gave up and installed the regualar ubuntu version and only after fixing the graphic drivers installed cinnamon. so if you won't find any way to stop nouveau
I'd go with installing fresh ubuntu and try again then install kde.

---

### Post by Yellow Pasque on 2013-02-09
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by MartianTek3 on 2013-02-10
Thanks I will try to install bumblebee

---

### Post by MartianTek3 on 2013-02-14
Ok Bumblebee is installed 

And previously I had the Nouveau driver removed as shown by n00ne 

But the problem is once i uninstalled that driver, the headers for my programs disappeared I will show ya what i mean... 


Should i reinstall Nouveau and start over ( not going to remove KDE)

:?:

---

### Post by MartianTek3 on 2013-02-15
I give up, buggers ](*,) 

1. I am going to install Ubuntu 12.10 64bit 

2. After the install i am going to need to install Bumblebee, correct? 

3. And with that, I should have a functional GPU 

4. Thank you all for your help:) 

5. Kubuntu, this is for you :-({|= 

6.This a good plan of action?

---

### Post by MartianTek3 on 2013-02-16
Wow what a experience  

With Much Deliberation and Head banging ](*,)  

I have morphed into a beautiful and gush tons simplified OS 

Ubuntu 12.10, Really takes computing to a whole new level 

1. Installed Updates 
2. Installed Bumblebee 
3. And is enjoying the Freedom in Simplicity 

Excuse me for the flowery language 

Solution Solved!!:rolleyes: 

When messing with the NVIDIA GT 540M graphics driver 

BACKUP your data (alot of installing issues) 
 
*Advanced NVIDIA users feel free to install the graphics driver(.run file) 
I certainly ran into too much problems with Nouveau and general system meltdown 

*Beginning NVIDIA Users 
Find the Bumblebee Project wiki page  
Follow the Instructions as given 
The tech people that made this project really knew what they are doing  
Bumblebee has integrated modules that boost GPU efficiency when in battery mode 

If Battery life is an issue, Install Jupiter 
Once i installed it I noticed clearly noticeable battery life 
from 1 hour originally to about 3 hours! 

Concluding, thank you all for assisting me:grin: 

-MartianTek3

---

