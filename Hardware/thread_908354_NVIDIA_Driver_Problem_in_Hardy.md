---
title: "NVIDIA Driver Problem in Hardy"
date: 2008-09-02
forum: Hardware
---

### Post by raywood on 2008-09-02
I have been trying to get an NVIDIA driver to work with Hardy.  I have an EVGA 256-P2-N624-AR GeForce 7900GS video card.  I have tried a number of combinations, including EnvyNG, following NVIDIA's driver install instructions, etc.  At present, I have a situation where GRUB does a normal boot, I see the Ubuntu loading screen, but before getting to the login screen, the monitor says "No Signal" and then I get a black screen and no further action from the hard drive light.  

Running recovery mode at bootup, and then running xfix, enables the system to boot normally, but System > Administration > Hardware Drivers shows no proprietary drivers in use by the system.  It appears that I need to use NVIDIA's proprietary drivers to run VMware Workstation and Google Earth properly.  But when I install them, it seems like I wind up back with an unbootable system.

---

### Post by in-dust-rial on 2008-09-02
i am not a pro, but you should
- boot the newer kernel, if you can choose
-xorg.conf  nvidia to nv (driver)
-and remove all the installed mess :D
-try 'nvidia-glx-new' package instead of the normal one.


-use xorg.conf backups
-report more deteils on your system if you want to get proper help

if the automatic installation of ubuntu for binary drivers, doesn't help, try:
```
https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia
```
good luck

---

### Post by raywood on 2008-09-02
Thanks for your reply.  I'm not sure what the newer kernel is, and I don't know what additional details you would like.  Also, what do you mean by "xorg.conf nvidia to nv"?  

I appreciate the tip about nvidia-glx-new, but I got the impression somewhere that that driver was no longer "new."  I'll try again with that, though, and I'll also look at your recommended link.

---

### Post by raywood on 2008-09-02
I tried nvidia-glx-new.  In my search of Synaptic, it is the only nvidia-related package installed other than jockey, so I don't know if there's any "mess" to remove.  I'm open to more specific explanation on that.

I had previously visited the website you recommended.  It may be outdated.  It seems to be recommending a driver, 169.12, that differs from the one that EnvyNG tries to install and that NVIDIA's webpage recommends, which is 173.14.12.

---

### Post by in-dust-rial on 2008-09-02
```
BinaryDriverHowto/Nvidia (last edited 2008-08-18 11:27:13 by sitsofe)
```
but maybe it is not up to date, and just smaller changes had been made.

but the side says, that your card is not soupported by HARDY restricted drivers(8.04)!

```
http://ubuntuforums.org/showthread.php?t=265956
```
here they say it is soupported ( but on a nvidia site)

at least this thing may help you:
```
http://ubuntuforums.org/showthread.php?t=500202
```

and then maybe this?
```
http://packages.ubuntu.com/de/intrepid/nvidia-glx-96
```


-the newer kernel is maybe 2.6.24-19-generic
or a number higher then the otherones!

in xorg.conf the line driver:
```
Section "Device"
    Identifier     "nVidia Corporation NV25 [GeForce4 Ti 4200]"
    Driver         "nv"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
EndSection
```
says what driver you are useing and as far as i remember 'nv' is the default opensource one... which should be still working.

i am not a pro, so i dont know how to totally remove stuff from older installations!

-additional data would be, used kernel and 
$dmesg | tail
complete xorg.conf
the /var/log/Xorg.0.log    
$lsmod | grep -i nv

use a pastebin!
maybe you can just google for the errors in the log!


good luck

---

### Post by Tindytim on 2008-09-02
I had some issues installing Drivers also.

From another thread:
> **Tindytim said:**
> 
***_[COLOR="Red"]I got this working by downloading the Nvidia drivers from the site and installing them manually (I'll show how I did that at the bottom).[/COLOR]_***

I then turned on the Separate instances of X (Using Nvida X Server Settings, which are installed with the Drivers Automatically). How ever in order for that to work you need to open it within the console by typing:
```
sudo nvidia-settings
```
This can by typed in any directory. Then apply and save the settings to your Xorg file. Restart, then apply Twin-View again (using "sudo nvidia-settings") then Restart. **It may work if you just apply Twin-View with "sudo nvidia-settings" at first, then restart. (might as well try it first).**.

**_And now for installing the Nvidia Drivers manually:_**
***1.)*** Download the Nvidia Drivers to your Desktop

***2.)*** Press Crtl+Alt+F1. This will take you out of the GUI (not sure on the specifics).

***3.)*** Now type in:
```
sudo /etc/init.d/gdm stop
```Which will shutdown the **G**nome **D**isplay **M**anager (and consequently X). The Nvidia Drivers don't install unless X isn't running.

***4.)*** Now to get to the Drivers. Type:
```
cd Desktop
```cd is the command to **c**hange **d**irectory (which works in DOS). In this case, you go from the home directory to the Desktop directory within the home directory (where the terminal normally starts). Your command line should now say something like
```
[user]@[computer]:~/Desktop$
```Where [user] and [computer] are the names of the user and computer respectively.

***5.)*** Now simply type
```
dir
```
Which stands for **dir**ectory (also works in DOS), and lists all the files and directories within the directory you're in. From there is should be easy to type in the file name of the driver.

***6.)*** as the Nvidia site says:
```
sudo sh [Driver]
```
Where [Driver] is the driver name (I had "NVIDIA-Linux-x86_64-173.14.12-pkg2.run" so expect something similar).

From there I was told that the Driver couldn't find any pre-existing compatible driver (or something like that) and said it would compile one on the spot. It's been working great!!!

**_Lib-c Header Files_**
I got an error about this and freaked. The Solution was as simple as typing:
```
sudo apt-get install build-essential
```
into the terminal.

---

