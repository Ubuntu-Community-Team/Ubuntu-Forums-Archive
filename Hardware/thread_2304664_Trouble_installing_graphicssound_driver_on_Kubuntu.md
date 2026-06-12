---
title: "Trouble installing graphics/sound driver on Kubuntu"
date: 2015-11-28
forum: Hardware
---

### Post by darth.jon09 on 2015-11-28
Hi,

I have a Toshiba Satellite C50D-B-12C with processor AMD A4-6210 APU with AMD Radeon R3 Graphics.

Also, I have installed Kubuntu 14.04.3 64-bit.

In my first install I downloaded AMD Radeon Software Crimson Proprietary Ubuntu 14.04 x86_64 Minimal Video Driver for Graphics Accelerators (Non-X Support) from the official site of AMD and installed the driver. But after I restarted the laptop I got a black screen and although I waited a long time, nothing happened.

So, I have reinstalled Kubuntu and now I don't know what to do to get my graphics driver in use for Kubuntu.

Also another thing is that I can't control the sound from the keyboard even though I get the pop up which shows the volume decreasing, this doesn't affect the volume at all.

[ATTACH=CONFIG]265813[/ATTACH]

Thank you for any help or suggestion. :)

---

### Post by tridentlead on 2015-11-29
I have never used an AMD card but I believe the following still applies. Go into terminal and run:
```

sudo kubuntu-drivers list

```
This command lists all the drivers applicable to your entire device(not just your GPU). You can then run either:
```

sudo kubuntu-drivers devices 

```
or
```

sudo kubuntu-drivers autoinstall 

```
the former will list the driver packages for your devices, which you can install with:
```

sudo apt-get install {whatever}

```
the latter will automatically install the packages it deems best for your system.

Note: I think the package for kubuntu is kubuntu-drivers, if that does not work try ubuntu-drivers

---

### Post by darth.jon09 on 2015-11-29
> **Daniel_Stutman said:**
> I have never used an AMD card but I believe the following still applies. Go into terminal and run:
```

sudo kubuntu-drivers list

```
This command lists all the drivers applicable to your entire device(not just your GPU). You can then run either:
```

sudo kubuntu-drivers devices 

```
or
```

sudo kubuntu-drivers autoinstall 

```
the former will list the driver packages for your devices, which you can install with:
```

sudo apt-get install {whatever}

```
the latter will automatically install the packages it deems best for your system.

Note: I think the package for kubuntu is kubuntu-drivers, if that does not work try ubuntu-drivers

Hi,

Thank you for your reply. When I typed
```

sudo kubuntu-drivers list

```
the output was "command not found". So, as you suggested I tried
```

sudo ubuntu-drivers list

```
which gave me "fglrx-updates, fglrx".

Then I typed
```

sudo ubuntu-drivers autoinstall

```
which gave me "No drivers found for automatic installation".

---

### Post by brianewalsh2 on 2015-11-30
Ive never used and AMD card on ubuntu, but I know that I will experience the same issues on boot when I first switch to an Nvidia driver after a fresh install. 

For me to get to the desktop, I will have to add the boot flag 'nomodeset' to get it to boot properly. You then will need to update grub with it so you dont have to type it at every boot.

follow the steps in this link [http://ubuntuforums.org/showthread.php?t=1761252](http://ubuntuforums.org/showthread.php?t=1761252)

---

