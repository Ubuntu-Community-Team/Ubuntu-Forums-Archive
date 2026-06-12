---
title: "Can't find firmware for ATI/AMD RV710/730"
date: 2017-08-15
forum: Hardware
---

### Post by mmmmna on 2017-08-15
My system board has onboard nVidia graphics, but I'm not connected to that display port, I am connected to my Radeon 4350 card which I added into the system.

When I tested the live session that I put on my Flash drive, EVERYTHING I discuss herein worked as expected, so I installed Ubuntu Mate 16.04.3.

I can only boot my fresh install of Ubuntu Mate 16.04.3 by using a recovery mode, then simply exiting the recovery screen to get a functional (but not optimal) Mate desktop environment. Thankful that much is working, so I can get stuff installed via GUI.

The only error messages I see when normal boot fails involves 2 lines showing something about namespace lookups with ACPI elsewhere in the same string, and the final message of the only 3 messages says something about needing firmware in order for the kernel to do mode switching. The system stays there for more than 4 hours, so it is frozen. Reinstalled, still same. 

These errors appear on screen but there is no ability to switch to other consoles, ctrl-alt-f# does nothing at all, alt-f# also does nothing (in case this distro uses alternative console keystrokes). For any effort to switch consoles, the error text is not altered, so maybe all consoles display the same?

When I have rebooted into recovery mode, my screen resolution is set at 1280 x 1024, which looks like a default value, and my display is listed as 'unknown', and thus is not detected at all.

While I was installing, the live session had higher display resolution and also had the correct name of my display, which is an Acer X223W.

I'm working under the assumption that fixing the final boot error message saying needing firmware for AMD/ATI greater than R600 will also correct the issues I'm seeing in the limited recovery mode, if in fact the fix is not also going to correct the normal boot issue and corrects resolutions for all boot modes.

From there, my research seems to point me to getting a package named 'linux-firmware-nonfree' to be installed in my current system.

I launched my Synaptic package manager (installed from console using sudo apt-get install synaptic), I refreshed my repositories and found nothing that matches my needed package.

Here is the repository list I'm using (lines beginning with # were removed for brevity, I did read those comments):
```
cat /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu xenial partner
deb http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse

```

I have found the following [https://packages.ubuntu.com/search?keywords=linux-firmware-nonfree](https://packages.ubuntu.com/search?keywords=linux-firmware-nonfree)
and I assumed that those are the latest packages for linux-firmware-nonfree and I assumed that they contained what I needed, since I was told in the boot message I needed that exact package.

AMD/ATI is not listed as a file within either package found in that link.

Aside from suggesting maybe there needs to be error checking hereabouts, anyone know where I will actually find the nonfree firmware files for my Radeon 4350?

TIA, sorry for the long post but I addressed a lot of possibilities to get where I am and potential suggestions might need to know what I've seen and done. Details help, right?

---

### Post by vocx on 2017-08-15
> **mmmmna said:**
> My system board has onboard nVidia graphics, but I'm not connected to that display port, I am connected to my Radeon 4350 card which I added into the system.

...

I'm working under the assumption that fixing the final boot error message saying needing firmware for AMD/ATI greater than R600 will also correct the issues I'm seeing in the limited recovery mode, if in fact the fix is not also going to correct the normal boot issue and corrects resolutions for all boot modes.

Aside from suggesting maybe there needs to be error checking hereabouts, anyone know where I will actually find the nonfree firmware files for my Radeon 4350?

TIA, sorry for the long post but I addressed a lot of possibilities to get where I am and potential suggestions might need to know what I've seen and done. Details help, right?
Did you read this page? [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

It seems the Radeon 3450 is supported by the "radeon" driver which should be automatically installed in 16.04. Maybe you ought to try the "amdgpu" module as well. [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)

I don't know about any firmware files. I assume if your card is supported by "radeon" the firmware should already come with your kernel. Maybe make sure "linux-firmware" is installed. At least in my system, there is no "linux-firmware-nonfree".

---

### Post by Yellow Pasque on 2017-08-15
The radeon firmware files are part of the linux-firmware package and are included in the install .iso
You should not need to do anything to install firmware for radeon cards, except for perhaps the very newest ones.

You can verify you have the necessary files as the following command should print out 4 entries:
```
ls -la /lib/firmware/radeon/RV71*
```

If the firmware is missing, then try to reinstall the appropriate package:
```
sudo apt-get install --reinstall linux-firmware
```

My guess is that your firmware messages are a symptom rather than a cause.

---

### Post by QIII on 2017-08-15
Neither the open source AMDGPU nor the AMDGPU-PRO overlay will work with that hardware.  Do not attempt to install.  fglrx will no longer work with recent distros with the current X.

The radeon driver has been installed by default and that is the only driver available.

---

### Post by mmmmna on 2017-08-15
Ok, thanks to everyone for the responses, it seems the drivers are installed.
Might be a bit of a show. :popcorn:

In recovery mode, I see ls -la /lib/firmware/radeon/RV71* showing this:> ls -la /lib/firmware/radeon/RV71*
-rw-r--r-- 1 root root   5440 Mar 29 20:46 /lib/firmware/radeon/RV710_me.bin
-rw-r--r-- 1 root root   3392 Mar 29 20:46 /lib/firmware/radeon/RV710_pfp.bin
-rw-r--r-- 1 root root  16160 Mar 29 20:46 /lib/firmware/radeon/RV710_smc.bin
-rw-r--r-- 1 root root 116120 Mar 29 20:46 /lib/firmware/radeon/RV710_uvd.binThanks Temüjin, the files I was hoping needed to be installed appear to have been installed as you folks suspected. I'm still clueless.

Again, while running in recovery mode:
> dmesg | egrep 'drm|radeon'
[    1.550337] [drm] Initialized
[    1.593520] [drm] VGACON disable radeon kernel modesetting.
[    1.593680] [drm:radeon_init [radeon]] *ERROR* No UMS support in radeon module!
[   12.264774] [drm] VGACON disable radeon kernel modesetting.
[   12.264877] [drm:radeon_init [radeon]] *ERROR* No UMS support in radeon module!Would those errors be important here?




To complete the requested output: lspci -nn | grep -E 'VGA|Display'
> lspci -nn | grep -E 'VGA|Display'
00:0d.0 VGA compatible controller [0300]: NVIDIA Corporation C61 [GeForce 6100 nForce 405] [10de:03d1] (rev a2)
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV710 [Radeon HD 4350/4550] [1002:954f]I'd really not want to remove the AMD/ATI card. So many installs of a half dozen versions of as many distros used to always get this same hardware set up correctly, doing so with no intervention from me. 
I'm only using recent Debian derived distros which are having issues with this hardware.


In regards RadeonDriver, does the ls -la output at the start of this post answer the issue?
In regards amdgpu, Synaptic shows libdrm-amdgpu1 and xserver-xorg-video-amdgpu-hwe-16.04 are listed as installed.

Will marked solved in a few hours, unless someone tells me the graphics are still not correctly installed.


Since boot logs are written to for both cases of 1] the recovery mode attempts which succeed and 2] the earlier failure modes which do not succeed, I'll need to have a clue about which logs to search and where inside the log files are the reports of the default mode boots which fail.

---

