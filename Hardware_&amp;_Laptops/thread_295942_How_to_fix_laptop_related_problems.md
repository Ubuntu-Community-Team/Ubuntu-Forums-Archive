---
title: "How to fix laptop related problems"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by lingnoi on 2006-11-08
I have updated this list of problems that you may come across for laptops. This list is primarily for the Samsung Laptops (because that is what I am using).

Problems:

**fn+up and fn+down (Brightness up and down) doesn't work with the Nvidia 3D driver**

Updating your BIOS could solve this problem. On the Samsung R55 updating your BIOS to the latest version will fix this problem.

**The volume keys on my laptop control the wrong volume level. (Feisty)**

Go to System->Preferences->Sound

Under the 'devices' tab click on which volume you wish to control in the "Default Mixer Tracks"


**Horrible noises comming out of the speakers whenever you login or open a program (Dapper / Edgy)**

Type:

```
sudo gedit /etc/modprobe.d/alsa-base
```

Add the following line to the bottom of the file:

```
options snd-hda-intel position_fix=1 model=3stack
```

**I want my screen 1280X800 (widescreen)**

Type:
```
sudo gedit /etc/X11/xorg.conf
```

Find the text area with all the screen resolutions and add 1280x800 to this list.

**The Ubuntu logo doesn't display when I shutdown (Dapper Only)** 

Type: 

```
sudo gedit /boot/grub/menu.lst
```

Change vga=789

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=vga=789 quiet splash
```

---

