---
title: "GPU Installation: Desktop Does Not Load Unity Afterwards"
date: 2014-07-14
forum: Hardware
---

### Post by GreenRaccoon on 2014-07-14
I've got a weird problem after installing a new GPU in my desktop. Everything goes awesome until I log into Ubuntu. After I type in my password and log in, all that shows is my wallpaper and mouse cursor: there is no panel or unity dash. I can move my cursor around the screen, but a right-click does not trigger the usual cursor menu. Keyboard shortcuts also do not work. Before I installed the GPU, I did the usual apt-get update and apt-get upgrade, so everything not-GPU-related should be up to date.

Isn't this weird? I was expecting either everything to work or nothing to work at all, but what happened was somewhere in between. I'm guessing there's a little, trivial thing I overlooked or forgot to do.

Previously, I just had an APU, and now I've added a GPU into a PCI slot. So both an APU and a GPU are running. (They're compatible with each other too; I checked.) I also installed a new power supply at the same time, but I doubt that would make a difference.

Any ideas before I do a fresh install? Keep being awesome, Ubuntu men.

Here's my tech specs:
OS: Ubuntu 14.04 64 bit
APU: AMD Kaveri A10-7850K
GPU: AMD Radeon HD7970 (Sapphire)
RAM: 8GB

---

### Post by mooreted on 2014-07-14
Found this online:

I had a similar problem, I solved it by switching in terminal (CTRL+ALT+F1) then removing the configuration file ~/.config/dconf/user like this :

sudo service lightdm stop
rm ~/.config/dconf/user
sudo service lightdm start

What this does is causes the OS to create a new desktop configuration for the user. This will reset your settings to defaults.

---

### Post by grahammechanical on 2014-07-14
And what video driver did you have activated before you made the hardware change? An open source video driver or a proprietary video driver? Which adapter is running? The APU or the GPU?

Regards.

---

### Post by GreenRaccoon on 2014-07-15
> **mooreted said:**
> Found this online:

I had a similar problem, I solved it by switching in terminal (CTRL+ALT+F1) then removing the configuration file ~/.config/dconf/user like this :

sudo service lightdm stop
rm ~/.config/dconf/user
sudo service lightdm start

What this does is causes the OS to create a new desktop configuration for the user. This will reset your settings to defaults.
Choice as! I already did a clean install of Ubuntu, but I'm still having problems getting the drivers from AMD's website to work. I'll try that out tonight. I'm guessing that'll work cause right now my problem is that, after I login, the xserver crashes and resets itself back to the login screen. So basically it's the login that never ends.

> **grahammechanical said:**
> And what video driver did you have activated before you made the hardware change? An open source video driver or a proprietary video driver? Which adapter is running? The APU or the GPU?

Regards.
I can't remember exactly. I know I was using fglrx-updates for a bit, but I think I installed the 12.4 Catalyst driver from AMD's website.

Which adapter exactly? Like which one my monitor is connected to? My HDMI cord is plugged into the GPU. It doesn't seem to work if I plug it into the HDMI port on the motherboard while the GPU is installed.

Thanks for the help, men!

---

### Post by QIII on 2014-07-15
Hello!

By default, Ubuntu installs without the file /etc/X11/xorg.conf.  The open source driver does not need that file as it used to.

However, when you install a proprietary driver, that file** *is*** required.  In your case it is especially necessary because you have multiple GPUs.  I'm going to assume for the moment that you have a clean install -- and only one install -- of the fglrx driver.

For AMD/ATi GPUs (in your case more than one), that file is created by issuing the following command:

```
sudo amdconfig --adapter=all --initial
```

There are posts aplenty saying this is no longer necessary, but given the number of times I have had to help people out by doing this I am convinced it still is.

Since you are unable to reach a GUI, you will probably have to go to Recovery mode to reach the command line.

(The following is from memory -- probably faulty):

To do that, press and hold SHIFT (can't remember if it's left or right SHIFT at the moment).  That will bring you to the GRUB menu.  Select "Advanced Options".  Under that, select Root.  At the root prompt, mount your system in read/write mode

```
mount -o remount,rw /
```

You may now issue the command, but you need not include the sudo.  So:

```
amdconfig --adapter=all --initial
```

Reboot and let us know what the result is.

---

### Post by GreenRaccoon on 2014-07-19
> **QIII said:**
> Hello!

By default, Ubuntu installs without the file /etc/X11/xorg.conf.  The open source driver does not need that file as it used to.

However, when you install a proprietary driver, that file** *is*** required.  In your case it is especially necessary because you have multiple GPUs.  I'm going to assume for the moment that you have a clean install -- and only one install -- of the fglrx driver.

For AMD/ATi GPUs (in your case more than one), that file is created by issuing the following command:

```
sudo amdconfig --adapter=all --initial
```

There are posts aplenty saying this is no longer necessary, but given the number of times I have had to help people out by doing this I am convinced it still is.

Since you are unable to reach a GUI, you will probably have to go to Recovery mode to reach the command line.

(The following is from memory -- probably faulty):

To do that, press and hold SHIFT (can't remember if it's left or right SHIFT at the moment).  That will bring you to the GRUB menu.  Select "Advanced Options".  Under that, select Root.  At the root prompt, mount your system in read/write mode

```
mount -o remount,rw /
```

You may now issue the command, but you need not include the sudo.  So:

```
amdconfig --adapter=all --initial
```

Reboot and let us know what the result is.

Thanks QIII. I never got to try your suggestion unfortunately because I went ahead and reinstalled Ubuntu. Your suggestion probably would have been WAY easier.

The legacy driver worked great after I reinstalled Ubuntu, but a program I wanted to run wouldn't work with that driver. The proprietary drivers were giving me some trouble too, so it was a bit of a battle. I tried installing the 12.4, 12.6, 12.8, and 14.4 AMD Catalyst drivers, and all of them had problems. But ironically, the 14.6 Beta driver works amazing. Who would have thought?

---

