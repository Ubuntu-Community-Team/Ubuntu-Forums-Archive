---
title: "1440x900 Resolution not available after update"
date: 2008-07-19
forum: Hardware
---

### Post by roboa1983 on 2008-07-19
Hi
I've been unsuccesfully trying for answers to this problem:
Yesterday, I downloaded some updates (I'm running ubuntu 8.04), and now, my screen resolution is lost. The maximum resolution available is 800x600, using my old xorg.conf or a vanilla one (modified to include 1440x900).
I attach the xorg.conf I have been working with.
```
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Modes           "1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection


```

It seems I have an nVidia GeForce 6100 Graphics Card (lpsci says so, although I am unable to download any drivers:
manually: when I try to install it from the nVidia webpage, it does not let me.
synaptic: I cannot download nvidia-glx or nvidia-glx-new, because of an xserver-xorg-core problem on synaptic (or for that case on apt-get). 

Lastly, I have tried reseting the xorg.conf as well as downloaded the drivers as I mentioned above.

Thanks for the help.

---

### Post by cherva on 2008-07-19
Why don't you try to install the dirvers with envy [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by roboa1983 on 2008-07-19
Hi cherva:
I forgot to mention, I also gave envy a shot. I downloaded it from the webpage and from synaptic and both of them had an error which stated that envy could not be run in my system (I have x86_64), which is weird, because I know that this is supported by envy.
Thanks for the help

---

### Post by warp99 on 2008-07-19
In the "Device" section add the following:

```
Driver	"nvidia"
```

but before you do that make sure you have the correct restricted drivers version for your running kernel. So open a terminal and type the following:

```
sudo apt-get install linux-restricted-modules-$(uname -r)
```

if you have the current modules it will tell you so. If not they will install, then just reboot to load the new drivers.

Edit:

What's the error message with this problem:

> synaptic: I cannot download nvidia-glx or nvidia-glx-new, because of an xserver-xorg-core problem on synaptic (or for that case on apt-get).

If you fix this first solving you other problem with the resolution will be much easier.

---

### Post by roboa1983 on 2008-07-19
Hi warp99. 
```
uname -r
 2.6.26-4-generic
```,
Which has no linux-restricted-modules equivalent. I already have installed the closets module (2.6.24-19). 
I added the nvidia part to the Device section and restarted, but it did not work. 
I've tried to look around for other solutions, but none seem to work.
For reference, this is an Acex X191W monitor.

Thanks!!

---

### Post by roboa1983 on 2008-07-19
```
$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx: Depends: xserver-xorg-core (>= 1:0.99.0-1) but it is not going to be installed
E: Broken packages

```
I have xserver-xorg-core, so I don't understand what the problem is: should I reinstall?

---

### Post by warp99 on 2008-07-19
> I have xserver-xorg-core, so I don't understand what the problem is: should I reinstall?

Well the version you're using is an older version according to apt-cache:

```
 apt-cache policy xserver-xorg-core
xserver-xorg-core:
  Installed: 2:1.4.1~git20080131-1ubuntu9.2
  Candidate: 2:1.4.1~git20080131-1ubuntu9.2
  Version table:
 *** 2:1.4.1~git20080131-1ubuntu9.2 0
        500 http://us.archive.ubuntu.com hardy-updates/main Packages
        500 http://security.ubuntu.com hardy-security/main Packages
        100 /var/lib/dpkg/status
     **2:1.4.1~git20080131-1ubuntu9 0**
        500 http://us.archive.ubuntu.com hardy/main Packages

```

Make sure you have the hardy-updates and hardy-security repositories enabled in the Synaptic Package Manager. With Synaptic open go to "Settings > Repositories > Updates" then make sure those repositories are enabled. Of course when you're done click "Reload" then "Mark All Upgrades" and finally "Apply".

---

### Post by roboa1983 on 2008-07-19
Well, this thread helped realize the problem. I couldn't find the hardy updates, because I have (for an unknown reason) been working with Intrepid Ibex.
Is there a way to revert this? Just go back to an old version in GRUB???

---

### Post by warp99 on 2008-07-19
> **roboa1983 said:**
> Hi warp99. 
```
uname -r
 2.6.26-4-generic
```,
Which has no linux-restricted-modules equivalent. I already have installed the closets module (2.6.24-19). 
I added the nvidia part to the Device section and restarted, but it did not work. 
I've tried to look around for other solutions, but none seem to work.
For reference, this is an Acex X191W monitor.

Thanks!!

That's is a newer kernel and you can't use the newer kernel with the older restricted-modules. **All of the kernel module packages** must end with the running kernel version.

So you either have to downgrade the kernel or build you own restricted modules:

[https://help.ubuntu.com/community/Kernel/Compile#Rebuilding%20%27%27linux-restricted-modules%27%27](https://help.ubuntu.com/community/Kernel/Compile#Rebuilding%20%27%27linux-restricted-modules%27%27)

---

### Post by warp99 on 2008-07-19
> **roboa1983 said:**
> Well, this thread helped realize the problem. I couldn't find the hardy updates, because I have (for an unknown reason) been working with Intrepid Ibex.
Is there a way to revert this? Just go back to an old version in GRUB???

Sure you can downgrade by replacing every occurrence of "intrepid" in you /etc/apt/sources.list to "hardy". The quickest way to do this is open a terminal and do the following:

```
sudo sed -i 's/intrepid/hardy/g' /etc/apt/sources.list
```

then issue 'sudo apt-get update' and then 'sudo apt-get dist-upgrade'. This should place you back to the point of an updated hardy distro.

---

### Post by roboa1983 on 2008-07-20
I try to do the steps you mention, but after putting 
```
sudo apt-get dist-upgrade
```
It doesn't install anything. 
Therefore, /etc/apt/sources.list has all hardy writing, but nothing has changed.
I tried installing the nvidia driver, and it states: 
```
ERROR: Unable to find the kernel source tree for the currently running kernel. Please make sure you have installed the kernel source files for your kernel and that they are properly configured;
```
And so on...
It's really strange that all of this happened. 
Thanks for the help...

---

### Post by warp99 on 2008-07-20
> **roboa1983 said:**
> I try to do the steps you mention, but after putting 
```
sudo apt-get dist-upgrade
```
It doesn't install anything. 
Therefore, /etc/apt/sources.list has all hardy writing, but nothing has changed.
I tried installing the nvidia driver, and it states: 
```
ERROR: Unable to find the kernel source tree for the currently running kernel. Please make sure you have installed the kernel source files for your kernel and that they are properly configured;
```
And so on...
It's really strange that all of this happened. 
Thanks for the help...

Well then you can revert to a previous kernel like this:

Boot up the computer as your would normally. When the grub menu starts to load quickly press 'escape' and choose a previous kernel to boot from. You should have a list to choose from so pick '2.6.24-19-generic'

Once you've loaded the desktop open a terminal and issue the following:

```
sudo apt-get remove --purge linux-image-2.6.26-4-generic
```

that will remove the intrepid kernel and reconfigure you grub menu to boot to the next highest kernel, which is 2.6.24-19-generic. All of your modules should now work since they match the running kernel.

---

