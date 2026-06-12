---
title: "Simple steps to install GeForce GTX 750Ti on Ubuntu Gnome 14.04"
date: 2014-11-15
forum: Hardware
---

### Post by zircon_34 on 2014-11-15
It took me several hours to find this out as I am quite new to linux. Was a bit frustrating but now I am greeted with beautiful graphics. hope this helps as reference in a condensed way. Some of the commands I am not sure what they meant (*) but am learning :popcorn: any comments would enhance the thread greatly!

Simple steps to install GeForce GTX 750Ti on Ubuntu Gnome 14.04:

a) go to nvidia.com and download driver to your home folder (I used NVIDIA-linux-x86_64_340.58)

b) For Nvidia to find linux header files (*):
```
 sudo apt-get install build-essential linux-headers-$(uname -r)
```

c) To enable full screen text mode (nomodeset):
```
 sudo gedit /etc/default/grub
```
Edit GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
Save it
```
 sudo update-grub
 reboot
```
Your screen may have a weird resolution at this stage, dont worry...

d) Switch to command line mode (Press Ctr-Alt-F1), login using your username and password, disable the graphical interface and install the driver:
```
sudo service gdm stop
``` 
if the console hangs, press ctr+alt+F1
```
sudo chmod +x NVIDIA-Linux-x86_64-334.21.run
```
run the install script
```
sudo sh NVIDIA-Linux-x86_64-334.21.run
```
e) restart the graphical user interface
```
sudo service gdm start
```

Let me know if this works for you too!

---

### Post by MartyBuntu on 2014-11-15
Any reason you wouldn't use the Software Manager to do this?

---

### Post by zircon_34 on 2014-11-15
Yes, because additional drivers were not available in the software sources (using softare center)... and actually I had the same situation on a notebook with nvidia grafic card. No additional drivers available, so I tried once to install the drivers available in synaptic and it messed my install. I wish the process was more simple like click and install.

---

### Post by oldfred on 2014-11-15
Generally the nVidia drivers are in the repository. 
But a very new card may need the latest nVidia driver and the versions in the repository will typically be a version or two older.
So to have newest card work or work well may have to be installed from nVidia. But there are ppa that have the most recent driver and often you may also need support software and even the newest kernel for newest driver to work.

       Install Nvidia 340.24 from ppa:xorg-edgers/ppa
[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)
All the current drivers
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)
New kernels ppa
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
xorg-edgers PPA
Oibaf PPA discusion
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)
Ubuntu Kernel Mainline PPA
[http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1)
[https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed](https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed)

---

### Post by zircon_34 on 2014-11-16
Oldfred, is there an advantage to install the unsupported ppa over self installing the driver? I guess it has to do with future updates correct?:p

Again, newbie, bear with me...

I was wondering, my graphic driver seems to have installed correctly, I have the NVIDIA X Server Settings program installed when I look in my software menu (green NVIDIA icon). However, when I look in synaptic package manager in preferences (software and updates), I cannot see the NVIDIA driver in additional driver.

Is this normal? How can I check on the command line if the driver is installed? do I also need to disable the nouveau driver to avoid any future conflicts between both driver (I guess the NVIDIA tool disable this during install)?

---

### Post by oldfred on 2014-11-16
I think the advantage of a ppa is ease, but you must trust ppa as it automatically keeps updating if the creator adds new versions.
Ubuntu integrates video into kernel with dpkg. If you install directly from nVidia, I think you still have to manually rerun that part of install task with each kernel update or video stops working. With ppa it is automatic.
And that is why you do not see it in synaptic nor any dpkg commands.

---

### Post by pqwoerituytrueiwoq on 2014-11-16
> **oldfred said:**
> I think the advantage of a ppa is ease, but you must trust ppa as it automatically keeps updating if the creator adds new versions.
Ubuntu integrates video into kernel with dpkg. If you install directly from nVidia, I think you still have to manually rerun that part of install task with each kernel update or video stops working. With ppa it is automatic.
And that is why you do not see it in synaptic nor any dpkg commands.you do, iv done it before
i prefer to get my driver from the xorg edgers repo
the new 346.16 beta driver supports overclocking

this will let you know when there is a new kernel update unless you don't logout/reboot regularly, but is tries to simplify the install process
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

btw if you chmod +x the run file you don't have to type the sh part in the next command

---

### Post by bonzini on 2014-11-16
As a GTX 750 owner myself, I prefer to trust the PPA.  Why?

Well, using NVIDIA's excellent scripts is fine but you need to re-do things every time a new kernel comes down the pipe at you.  With the PPA, no such problem.

Of course YMMV!

---

### Post by zircon_34 on 2014-11-19
Is anyone using this card in hybrid mode? any links appreciated...:popcorn:

---

### Post by oldfred on 2014-11-19
I thought hybrid was a laptop with two video drivers out one video port.
Since a video card you cannot output the internal video thru the nVidia card, but thru the ports built into the motherboard.
Or you have to physically switch connections.

---

### Post by zircon_34 on 2014-11-20
true, so I guess the motherboard grafic card is redundant.... but on my notebook, I have an nvidia and intel, both switching depending on the graphic needed (this works in OSX). I dont know how they make that work though. Perhaps there is a bridge or something installed between both cards.

---

### Post by zircon_34 on 2014-11-30
> **oldfred said:**
> Generally the nVidia drivers are in the repository. 
But a very new card may need the latest nVidia driver and the versions in the repository will typically be a version or two older.
So to have newest card work or work well may have to be installed from nVidia. But there are ppa that have the most recent driver and often you may also need support software and even the newest kernel for newest driver to work.

       Install Nvidia 340.24 from ppa:xorg-edgers/ppa
[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)


After small Ubuntu update, I could not boot in the graphical user interface anymore. I tried to reinstall my nvidia driver, but I could not use ```
sudo service gdm stop
```
This time it would hang and had to do hard reboot, no chance to install the nvidia driver manually. Don't know why I could not stop gdm, weird. 

Ok, so I added a ppa (till now never did, prefer not to add too many repositories as I am still new to linux). I know I am hardheaded...

```
[COLOR=#000000][FONT=inherit]sudo add[/FONT][/COLOR][COLOR=#666600][FONT=inherit]-[/FONT][/COLOR][COLOR=#000000][FONT=inherit]apt[/FONT][/COLOR][COLOR=#666600][FONT=inherit]-[/FONT][/COLOR][COLOR=#000000][FONT=inherit]repository ppa[/FONT][/COLOR][COLOR=#666600][FONT=inherit]:[/FONT][/COLOR][COLOR=#000000][FONT=inherit]xorg[/FONT][/COLOR][COLOR=#666600][FONT=inherit]-[/FONT][/COLOR][COLOR=#000000][FONT=inherit]edgers[/FONT][/COLOR][COLOR=#666600][FONT=inherit]/[/FONT][/COLOR][COLOR=#000000][FONT=inherit]ppa
[/FONT][/COLOR][COLOR=#000000][FONT=inherit]
sudo apt[/FONT][/COLOR][COLOR=#666600][FONT=inherit]-[/FONT][/COLOR][FONT=inherit]get[/FONT][COLOR=#000000][FONT=inherit] update
[/FONT][/COLOR][COLOR=#000000][FONT=inherit]sudo apt[/FONT][/COLOR][COLOR=#666600][FONT=inherit]-[/FONT][/COLOR][FONT=inherit]get[/FONT][COLOR=#000000][FONT=inherit] install nvidia[/FONT][/COLOR][COLOR=#666600][FONT=inherit]-[/FONT][/COLOR][FONT=inherit]340[/FONT]
```

I added the org-edgers ppa, installed the nvidia driver, that worked.

Was there recently a kernel update???

---

### Post by oldfred on 2014-11-30
I have lost track, but I thought it was now
 sudo service lightdm stop

Or does that depend on verison of Ubuntu?

---

### Post by Jim_Menegay on 2014-11-30
I also tried to follow zircon_34's instructions, and also ran into problems at the "sudo service gdm stop" step.  So, I should just try again, substituting "lightdm" for "gdm"? I'm on 14.04.

---

### Post by oldfred on 2014-11-30
I believe so.

[http://unix.stackexchange.com/questions/131496/what-is-lightdm-and-gdm](http://unix.stackexchange.com/questions/131496/what-is-lightdm-and-gdm)
[http://itsfoss.com/switch-gdm-and-lightdm-in-ubuntu-14-04/](http://itsfoss.com/switch-gdm-and-lightdm-in-ubuntu-14-04/)

---

### Post by zircon_34 on 2014-11-30
before the last Ubuntu update I managed to overcome the "screen freeze" by pressing ctrl+Alt+F1 after stoping gdm, you might try this. However, adding the ppa might be a solution for you, which is perhaps more easy. I reallized, that every small update might screw the driver by doing the manual install, whereas adding the ppa should overcome this problem.

---

### Post by Yellow Pasque on 2014-11-30
Installing the driver manually from the nvidia site is never something I would recommend to others (or call "simple"). Unfortunately, Ubuntu's repo is lagging a good bit on the nvidia driver for the past 2 releases (stuck on 331.xx), but there are better alternatives than a manual install. I hear good things about this repo for those who just want a more recent nvidia driver without all of the other stuff in xorg-edgers: [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

> **zircon_34 said:**
> I reallized, that every small update might screw the driver by doing the manual install
That's what dkms is for (so binary modules like the nvidia driver automatically build when a new kernel is installed). If you had the dkms package installed beforehand, the Nvidia installer probably would have added the nvidia module to the dkms list for you: [http://us.download.nvidia.com/XFree86/Linux-x86/340.46/README/installdriver.html#RegisteringTheNda02d](http://us.download.nvidia.com/XFree86/Linux-x86/340.46/README/installdriver.html#RegisteringTheNda02d)

---

