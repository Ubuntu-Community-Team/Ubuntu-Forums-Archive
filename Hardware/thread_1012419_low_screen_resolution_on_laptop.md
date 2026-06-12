---
title: "low screen resolution on laptop"
date: 2008-12-15
forum: Hardware
---

### Post by Jeff k on 2008-12-15
Hello: I have a Ubuntu 8.04 installation on a laptop
from Linux Certified. It came with Ubuntu 8.04 but 
because of issues with internet connectivity I wanted
to install software from CD/DVD instead of from repository.
I have a friend who gave me a DVD that was included in a
published magazine. The System installed fine and is working
but there is an issue with screen resolution. It only displays
800X600. 

Literally, in the Hardware Drivers application under major category Device driver there is listed nvidia_new and the checkbox is checked and immediately to the right is a red
ball icon with 'Not in use' to the right of that.

running command specified
# lspci | grep -i
01;00.0 VGA compatible controller: nVidia Corporation Unkown device 0649
(rev a1)

What does the message 'Not in use' mean in the hardware drivers
panel? And why is the actual driver designation not listed?

I do web related design and server side development with
L.A.M.P(php)setup.
Thank you for advice, suggestions, instructions, etc
Jeff K 
------------------
from page at above link:
The link lists three drivers:
 Ubuntu Release     nvidia-glx-new nvidia-glx  nvidia-glx-legacy
 8.04 Hardy Heron  169.12               96.43.05    71.86.04
none of these are listed explicitly.
I am not concerned about 3D acceleration, just inadequate
screen resolution.

---

### Post by tommcd on 2008-12-15
> **Jeff k said:**
> 
I have a friend who gave me a DVD that was included in a
published magazine. The System installed fine and is working
but there is an issue with screen resolution. It only displays
800X600. 

What distro is on this DVD? And what version of that distro?
Post the output of:
```
lspci -v | grep -i VGA
```
Do you know what specifically what nvidia chip is on the laptop?

Also post your /etc/X11/xorg.conf file.

BTW, how are those laptops from Linux Certified? Would you recommend them?

And welcome to the Ubuntu forums!

---

### Post by Jeff k on 2008-12-16
To answer last question first: How are laptops from
Linux Certified? I am satisfied with the one I have
but oddly, the manufacturer is not labeled. It only
has the label Linux Certified. The model is LC2430S
and has Intel dual core processor. There was no hard-
ware manual included. The only indication of a source
for the machine (other than Linux Certified) is the 
label on the bottom that lists Compal Information
Technology Ltd and at the bottom, made in China, 
where else, these days. It has SCSI drives. The DVD
was included in a publication about Ubuntu and had
a double sided DVD with 32 bit 8.04 on one side and
64 bit 8.04 on the other side. I do not have the mag
to  hand at the moment, other wise I would give you
the exact title.
I have fixed and upgrade/installed components in a
few laptops without instructions and manuals, so am
not terribly concerned about no hardware manual as
long as I can get good specs. 
This machine has built in finger print scanner and
web cam, and a few other features.

lspci -v | grep -i VGA produces
(same as in the original post)+ (prog-if 00 [VGA controller])

I will have to copy and transfer xorg.conf and place in
another reply.

I do not know what nVidia chip is on it. The Hardware Driver
panel only lists nvidia_new

---

### Post by tommcd on 2008-12-17
Run in terminal **sudo lshw** (lshw = list hardware). See if this gives more info about what nvidia chip it is.
Also run **aptitude search nvidia-glx**. This will list all the nvidia-glx frivers in the Ubuntu repos. A "p" next to the package means it is purged (i.e., not installed). A "i" next to the package means it is installed. Since it is a newer laptop you likely have nvidia-glx-173 or nvidia-glx-177.

To see if the driver is working, run in terminal **glxinfo | grep -i direct**. If it returns "yes", then direct rendering is enabled. If it reports "no" then it is not.
See this from the Ubuntu wiki about enabling the nvidia driver, although you have already done this apparently:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
Also see this about fixing screen resolutions:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
Just to be safe, back up your xorg.conf first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by punkybouy on 2008-12-17
I have had good luck using envyNG to install video drivers.

---

### Post by Jeff k on 2008-12-18
sorry but this is getting to be a cat and mouse
game:

su <pw>
lshw
PCI (sysfs)
(command does not complete, no command prompt)

aptitude search nvidia-glx -> no out put,returns to
command prompt.

lspci | grep -i nvidia 
01:00.0 VGA comapitble controller: nVidia Corporation 
Unknown device 0649 (rev a1)
lspci | grep VGA
same output as lspci | grep -i nvidia.

lshw -C video -> same result as lshw
xrandr 
Screen 0: minimum 640 X 480 current 800 x 600 
maximum 800 x 600
default connected 800x600 0mm x 0mm
800x600     61.0*
640x480     60.0

I do not want to tell xrandr to use a high resolution
than is listed for fear of damage, but I know it is
capable of higher resolution. The only difference is 
the system and what ever esoteric config file setting
may be different.
I will have to go back to the Linux Certified site and
see if I can get the actual video card spec.

------
added: video for this machine is nVidia NV 9600M
I don't know if that is Gforce or one of the others.
------

Thanks Jeff K

---

### Post by tommcd on 2008-12-19
> **Jeff k said:**
> 
su <pw>
lshw
PCI (sysfs)
(command does not complete, no command prompt)

aptitude search nvidia-glx -> no out put,returns to
command prompt.
You should be using **sudo lshw**. Using the root password in Ubuntu is not recommended. The lshw command should work.
For nvidia-glx, have you enabled the universe and multiverse repos? You should get a list of nvidia drivers with **aptitude search nvidia-glx**.
> **Jeff k said:**
> 
I do not want to tell xrandr to use a high resolution
than is listed for fear of damage, but I know it is
capable of higher resolution. The only difference is 
the system and what ever esoteric config file setting
may be different.
I will have to go back to the Linux Certified site and
see if I can get the actual video card spec.
As long as the resolution is within your monitor's specs there should be no risk of damage. Anyway, the resolution is what you are trying to fix here.
> **Jeff k said:**
> 
added: video for this machine is nVidia NV 9600M
I don't know if that is Gforce or one of the others.

According to these pages:
[http://packages.ubuntu.com/intrepid/nvidia-glx-177](http://packages.ubuntu.com/intrepid/nvidia-glx-177)
[http://packages.ubuntu.com/intrepid/nvidia-glx-173](http://packages.ubuntu.com/intrepid/nvidia-glx-173)
The -177 and -173 both support the nvidia 9600M series.
Make sure you enable the universe and multiverse repositories:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
Then run "sudo apt-get update". Then try to enable the nvidia driver:
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)
If that doesn't work, I would probably just install nvidia-glx-177 and then run "sudo nvidia-xconfig" after first backing up my xorg.conf.

Also see this thread. These guys report the driver from nvidia.com works when installed via envy:
[http://ubuntuforums.org/showthread.php?t=879759&highlight=nVidia+NV+9600M](http://ubuntuforums.org/showthread.php?t=879759&highlight=nVidia+NV+9600M)
That thread is from Hardy though. I would think the drivers in Intrepid's repos would have support for your card.

---

