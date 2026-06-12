---
title: "Display Config Help - NVIDIA NVS 810 + NVIDIA QUADRO P4000"
date: 2020-09-12
forum: Hardware
---

### Post by phurious2 on 2020-09-12
I have a very annoying issue. When I live booted from the Ubuntu install USB, all 8 of my displays worked without issue, and I was able to configure the layout successfully in the "Live" session. Once I install Ubuntu, Only the displays (4) attached to my primary video card, the P4000, work. I should mention that this is with the nvidia-driver-450 installed. The nvidia settings show both video cards, and all the displays attached, but all of the displays connected to the NVS 810 are disabled, and cannot be enabled no matter what I try. I tried re-install Ubuntu, using ONLY xorg instead of the Nvidia proprietary driver. This *SEEMED* to work, but once I rebooted from the install the boot just hung there and I was forced to power off. When I restarted the machine it came up to the logon prompt, but was completely unusable. Only 4 displays were working, and the resolutions were so far off I could not click on anything or login.

---

### Post by TheFu on 2020-09-12
I think the installer uses F/LOSS drivers, but with 20.04, an attempt to install the proprietary drivers happens.  I don't know those specific nvidia cards, but my Quadro and older NVS cards lost support before 16.04 was released, so only the F/LOSS drivers worked at all and at a lower resolution.  

Randomly loading the latest nvidia driver directly from nvidia may not be a good idea.  Use **sudo ubuntu-drivers autoinstall** on 18.04 or later LTS releases.  If separate drivers are needed for each card, I don't know how nvidia will handle that conflict, or whether it can at all.

Probably want to start by posting some hardware and driver information here for people who deal with this stuff to interpret.
A few commands:
```
$ lspci -vk |perl -lne 'print if /VGA|3d/i .. /^[\w]*$/'
$ lshw -C video
```
Copy/paste those commands (without the $, which says run as a number userid) AND copy/paste the results back here, wrapped in 'code tags' ... just like 'quote tags', but with "code" instead of "quote".

---

### Post by CelticWarrior on 2020-09-12
Both should work with the latest drivers. Actually 450 is suggested at Nvidia's website.

---

### Post by TheFu on 2020-09-12
[https://www.nvidia.com/Download/driverResults.aspx/163238/en-us](https://www.nvidia.com/Download/driverResults.aspx/163238/en-us)
I tried to install these for my supported GT 1030 using the package manager. Nope.

```
$ sudo apt install  nvidia-450 nvidia-450-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia-450
E: Unable to locate package nvidia-450-dev
```

Also tried to use 
```
$ sudo ubuntu-drivers autoinstall
```

No joy.  But this is the OP's thread.

---

### Post by phurious2 on 2020-09-12
Here is the output from the 2 commands, as well as some screen caps to help illustrate. In the screen caps, all the displays on the Nvidia Quadro P4000 are connected and in use where as all the displays connected to the NVS 810 are unavailable.
[ATTACH=CONFIG]286942[/ATTACH][ATTACH=CONFIG]286943[/ATTACH][ATTACH=CONFIG]286944[/ATTACH][ATTACH=CONFIG]286945[/ATTACH]

---

### Post by phurious2 on 2020-09-12
> **TheFu said:**
> [https://www.nvidia.com/Download/driverResults.aspx/163238/en-us](https://www.nvidia.com/Download/driverResults.aspx/163238/en-us)
I tried to install these for my supported GT 1030 using the package manager. Nope.

```
$ sudo apt install  nvidia-450 nvidia-450-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia-450
E: Unable to locate package nvidia-450-dev
```

Also tried to use 
```
$ sudo ubuntu-drivers autoinstall
```

No joy.  But this is the OP's thread.

I used:
```
$ sudo add-apt-repository ppa:graphics-drivers/ppa
$ sudo apt-get update
$ sudo apt-get install nvidia-driver-450
```

---

