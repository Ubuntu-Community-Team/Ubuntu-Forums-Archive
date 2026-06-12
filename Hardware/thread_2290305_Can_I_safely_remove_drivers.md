---
title: "Can I safely remove drivers?"
date: 2015-08-11
forum: Hardware
---

### Post by Paul_Cambal on 2015-08-11
Hello everyone,
I just installed the latest nvidia-346 drivers, but I have big issues with it. I decided not to try tweaking with it, and tried out the X.org drivers. I must admit I got surprised how well they work. Now I opened up synaptic, and saw that I still have all the nvidia-304 packages installed. 
So here's my question: Can I uninstall them? Will it break the X.org driver? 
This way I could install wine :)
Thanks for your help ;)

---

### Post by dino99 on 2015-08-11
hello Paul,
your post is a complete non sense ;)
before writing wrong comments, take times to at least understand what the gui is showing you: the nvidia drivers are listed into synaptic as possible drivers you can activate.
but if you pay attention to the one installed (probably the 346) none of the others can be installed at the same time: fully impossible ;)

That said, X.org is a graphic component; not a driver
There is plenty of wikis/howtos to educate yourself if you have a doubt (these links below for example)

---

### Post by Paul_Cambal on 2015-08-11
Okay, I might be a newbie on this one, but still there's something I need to understand. 
I've gone to apps > preferences > additional drivers. I was using the nvidia-346 entry. 
As I had troubles with this one, I decided to enable another entry, which is xserver-xorg-video-nouveau
I rebooted, and now when I go back to the same place, the entry is changed to nvidia-304-updates.
Why is that?
My goal is to avoid using an nvidia propriatary driver for now.
Thanks again, 
and also please tell me about basic stuff, it looks like I know less than I thought I knew

---

### Post by dino99 on 2015-08-11
Well if you were starting by telling us with gpu is inside, and which trouble you get with nvidia-346, that should help a bit to give you more precise answer.
Other question: from where have you installed the nvidia-346 driver ? (always do from the ubuntu archive)

Again i beg you to pay attention at what you do and how: if you have activated 'nouveau' then you will not get '304' activated :
from Synaptic -> Settings (top menu) -> Repositories -> Additional Drivers: select the driver you want to activate (nouveau or 346) AND hit the 'Apply Changes' icon at the right bottom corner before closing the dialog box (otherwise your choice is not saved indeed)

---

### Post by Paul_Cambal on 2015-08-11
> sudo ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
vendor   : NVIDIA Corporation
modalias : pci:v000010DEd00000DE9sv00001043sd00002114bc03sc00i00
model    : GF108M [GeForce GT 630M]
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-340 - distro non-free
driver   : nvidia-304-updates - distro non-free
driver   : nvidia-340-updates - distro non-free
driver   : nvidia-304 - distro non-free
driver   : nvidia-346-updates - distro non-free
driver   : nvidia-346 - distro non-free recommended

I had installed the 346 driver from the ubuntu "control panel" as stated above.
The issues I got were: very low framerate, display issues, as well as screen tearing.
I will try installing drivers again from synaptic, but for now I swear that when I choose the xorg entry on the list, at next reboot, I will see it installed nvidia 304 instead.
I'll let you know more when I will be done with synaptic

EDIT: turns out synaptic shows up the same window than the one I used to do the changes. It looks like I'm stuck :/

---

### Post by dino99 on 2015-08-11
your card even support the latest 352 driver [http://www.nvidia.com/download/driverResults.aspx/87649/en-us](http://www.nvidia.com/download/driverResults.aspx/87649/en-us) so there is no reason it select 304 as a fallback

is your cpu model also provide an inside gpu ?  (see nvidia's optimus setting in such a case)

---

### Post by Paul_Cambal on 2015-08-11
Ok I'll give it a try. I first wanted to avoid having to install an nvidia driver, to avoid needing nvidia-libopencl1, so I could install wine without huge workarounds. I'll tell you how it goes.

---

### Post by Paul_Cambal on 2015-08-11
The driver installation failed:
> nvidia-installer log file '/var/log/nvidia-installer.log'creation time: Tue Aug 11 15:37:10 2015
installer version: 352.30


PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin


nvidia-installer command line:
    ./nvidia-installer


Using: nvidia-installer ncurses user interface
-> Detected 4 CPUs online; setting concurrency level to 4.
WARNING: You do not appear to have an NVIDIA GPU supported by the 352.30 NVIDIA Linux graphics driver installed in this system.  For further details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '1340' of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

Do I have to disable the X server first? If so, then how do I do?
Also, I have an integrated graphics card, that's maybe why it doesnt seem to find my nvidia card, because it's the discrete video card.

Ps: thanks for your help. 
Really

---

### Post by dino99 on 2015-08-11
Having the full details help to dig an issue ;)
but there are some borked configurations on that system; so start to clean the room:
from synaptic, disable the 'non ubuntu' repo (mainly ppa & third party sources), and check you does not have mixed version sources, then close synaptic & open a terminal

> sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get purge nvidia*

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
read that wiki and do what is explained; then continue

if you want to install the 352 driver, add the xorg-edgers ppa, update, install the driver (only) then deactivate the ppa and update again
> [https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

> sudo apt-get install nvidia-352
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by Paul_Cambal on 2015-08-12
> [COLOR=#333333][FONT=UbuntuMono]ls -l /sys/kernel/debug/vgaswitcheroo/switch[/FONT][/COLOR]

I don't appear to have this file :/
But the first step > [COLOR=#333333][FONT=UbuntuMono]grep -i switcheroo /boot/config-*[/FONT][/COLOR]
outputs
> /boot/config-3.13.0-34-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-3.13.0-35-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-3.13.0-61-generic:CONFIG_VGA_SWITCHEROO=y


However, now, it really looks like I have the xorg nouveau driver enabled.
Do you have any idea how I could switch gpus now?
Thanks again

---

