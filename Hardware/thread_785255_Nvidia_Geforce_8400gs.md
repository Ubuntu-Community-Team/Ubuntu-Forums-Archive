---
title: "Nvidia Geforce 8400gs"
date: 2008-05-07
forum: Hardware
---

### Post by Yudraciell on 2008-05-07
I am using 8.04
as the title says i am using an Nvidia 8400gs
 ubuntu doesnt detect it...well it does just as an unknown nvidia device

read the last line

00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
**07:00.0 VGA compatible controller: nVidia Corporation Unknown device 06e4 (rev a1)**

---

### Post by andyrue304 on 2008-05-07
Have you enabled and downloaded the restricted nVidia driver?

---

### Post by Yudraciell on 2008-05-13
> **andyrue304 said:**
> Have you enabled and downloaded the restricted nVidia driver?

yes but it makes it so i have a whopping 640x480 res and i cant see anything

I even downloaded the package installer from nvidia.com

same thing happened

---

### Post by tekniche on 2008-06-01
> **Yudraciell said:**
> yes but it makes it so i have a whopping 640x480 res and i cant see anything

I even downloaded the package installer from nvidia.com

same thing happened

I am having the same exact problem you described. I have been working on this for a while and cant get it figured out. HELP! I tried the latest nvidia drivers and the restricted drivers and still no progress. Any help would be greatly appreciated.

---

### Post by hotweiss on 2008-06-01
You have to use the new 173.08 drivers:

[http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html)

---

### Post by tekniche on 2008-06-01
> **hotweiss said:**
> You have to use the new 173.08 drivers:

[http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html)

I have tried these drivers among many others. I have also tried the newest drivers from nvidia 173.14.05 and all the way back to 100.14.11. There are no drivers on the nvidia site that I could find. Also nvidia, nvidia-glx, and nvidia-new packages still showing my screen res at 800x600. I will try this driver but I am sure that I have already. I will let you know how it goes. Thanks!

---

### Post by hotweiss on 2008-06-01
> **tekniche said:**
> I have tried these drivers among many others. I have also tried the newest drivers from nvidia 173.14.05 and all the way back to 100.14.11. There are no drivers on the nvidia site that I could find. Also nvidia, nvidia-glx, and nvidia-new packages still showing my screen res at 800x600. I will try this driver but I am sure that I have already. I will let you know how it goes. Thanks!

I don't think that's a driver problem, but an xorg problem. They are a little tricky to install. I'm sure the 173.14.05 drivers will fix your problem, it's just a matter of installing them correctly. I had the same problem, so I just stuck with 169.12.

---

### Post by tekniche on 2008-06-02
> **hotweiss said:**
> I don't think that's a driver problem, but an xorg problem. They are a little tricky to install. I'm sure the 173.14.05 drivers will fix your problem, it's just a matter of installing them correctly. I had the same problem, so I just stuck with 169.12.

Do you have any tips or urls that I could check for more information on the proper installation of the driver? That could be what I have been having a problem with all along. Thanks!

---

### Post by Nepherte on 2008-06-02
First you have to remove the nvidia drivers you installed earlier -> use synaptic and search for nvidia-glx. You'll probably end up uninstalling nvidia-glx-new.

In this post I give some instructions on how to install the nvidia driver downloaded from their website: [http://ubuntuforums.org/showpost.php?p=5101368&postcount=2](http://ubuntuforums.org/showpost.php?p=5101368&postcount=2)

---

### Post by tekniche on 2008-06-02
> **Nepherte said:**
> First you have to remove the nvidia drivers you installed earlier -> use synaptic and search for nvidia-glx. You'll probably end up uninstalling nvidia-glx-new.

In this post I give some instructions on how to install the nvidia driver downloaded from their website: [http://ubuntuforums.org/showpost.php?p=5101368&postcount=2](http://ubuntuforums.org/showpost.php?p=5101368&postcount=2)

Yes I have gone through the steps that you describe in the post. I have gone all the way through the un-installation of all of the open source nvidia drivers. I have tried multiple nvidia proprietary drivers and all of the open source (nvidia-glx and new)I am still not able to get my card to function properly.

---

### Post by hotweiss on 2008-06-03
> **tekniche said:**
> Yes I have gone through the steps that you describe in the post. I have gone all the way through the un-installation of all of the open source nvidia drivers. I have tried multiple nvidia proprietary drivers and all of the open source (nvidia-glx and new)I am still not able to get my card to function properly.

OK, I finally installed the new Nvidia drivers using these steps:

0. sudo apt-get remove nvidia*
1. Ctrl-Alt-F1
2. sudo /etc/init.d/gdm stop
3. sudo su
4. sh ./NVIDIA-Linux-x86-173.14.05-pkg1.run
5. go through all the prompts
6. restart

I also found an interesting thread about the new drivers:
[http://www.nvnews.net/vbulletin/showthread.php?t=113919](http://www.nvnews.net/vbulletin/showthread.php?t=113919)

Using the following command should speed up applications like Firefox:

> nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1

BTW, these drivers are a big improvement.

---

### Post by tekniche on 2008-06-03
> **hotweiss said:**
> OK, I finally installed the new Nvidia drivers using these steps:

0. sudo apt-get remove nvidia*
1. Ctrl-Alt-F1
2. sudo /etc/init.d/gdm stop
3. sudo su
4. sh ./NVIDIA-Linux-x86-173.14.05-pkg1.run
5. go through all the prompts
6. restart

I also found an interesting thread about the new drivers:
[http://www.nvnews.net/vbulletin/showthread.php?t=113919](http://www.nvnews.net/vbulletin/showthread.php?t=113919)

Using the following command should speed up applications like Firefox:



BTW, these drivers are a big improvement.

Unfortunately, I have followed these steps exactly as described in the past. I have actually gone as far as reconfiguring the xserver-xorg and the gdm. I also have the thread that you posted from nvnews bookmarked. :confused: I have no idea how to fix this. Any, any, any help would be GREATLY APPRECIATED.

---

### Post by hotweiss on 2008-06-03
> **tekniche said:**
> Unfortunately, I have followed these steps exactly as described in the past. I have actually gone as far as reconfiguring the xserver-xorg and the gdm. I also have the thread that you posted from nvnews bookmarked. :confused: I have no idea how to fix this. Any, any, any help would be GREATLY APPRECIATED.

You can also try this:

[http://ubuntuforums.org/showpost.php?p=4970051&postcount=2](http://ubuntuforums.org/showpost.php?p=4970051&postcount=2)

...and this:

[http://ubuntuforums.org/showpost.php?p=5082510&postcount=2](http://ubuntuforums.org/showpost.php?p=5082510&postcount=2)

---

### Post by tekniche on 2008-06-03
> **hotweiss said:**
> You can also try this:

[http://ubuntuforums.org/showpost.php?p=4970051&postcount=2](http://ubuntuforums.org/showpost.php?p=4970051&postcount=2)

...and this:

[http://ubuntuforums.org/showpost.php?p=5082510&postcount=2](http://ubuntuforums.org/showpost.php?p=5082510&postcount=2)

Still having the same issue. I tried the second one step by step because I thought it might be removing some packages that I may have missed, but no luck. Still looking... 2 weeks at least... for an answer. :(

---

### Post by hotweiss on 2008-06-04
> **tekniche said:**
> Still having the same issue. I tried the second one step by step because I thought it might be removing some packages that I may have missed, but no luck. Still looking... 2 weeks at least... for an answer. :(

Did you try doing all of these steps from a fresh install?

---

### Post by tekniche on 2008-06-04
> **hotweiss said:**
> Did you try doing all of these steps from a fresh install?

I have not tried this from a fresh install. I was hoping to avoid the hassle of reinstalling fresh. I have about 250 gbs of data that I would need to save externally or something to do a fresh install and don't really have the money to go get another drive. Is there a way to just reconfigure everything back to defaults and ensure that everything that could be causing a problem is un installed? Thanks.

---

### Post by Unix_Slayer on 2008-06-05
> **hotweiss said:**
> OK, I finally installed the new Nvidia drivers using these steps:

0. sudo apt-get remove nvidia*
1. Ctrl-Alt-F1
2. sudo /etc/init.d/gdm stop
3. sudo su
4. sh ./NVIDIA-Linux-x86-173.14.05-pkg1.run
5. go through all the prompts
6. restart

I also found an interesting thread about the new drivers:
[http://www.nvnews.net/vbulletin/showthread.php?t=113919](http://www.nvnews.net/vbulletin/showthread.php?t=113919)



Your first step should have been as follows:

```
sudo apt-get install build-essential
```


See this post ===>[http://ubuntuforums.org/showthread.php?t=819043]("http://ubuntuforums.org/showthread.php?t=819043")

---

### Post by tekniche on 2008-06-05
> **Unix_Slayer said:**
> Your first step should have been as follows:

```
sudo apt-get install build-essential
```


See this post ===>[http://ubuntuforums.org/showthread.php?t=819043]("http://ubuntuforums.org/showthread.php?t=819043")

Tried the steps including sudo apt-get install build-essential. no luck. I'm about to give up on ubuntu all together. :mad:

---

### Post by starcannon on 2008-06-05
If you like I'd be willing to VNC in and set it up for you.

PM me if interested.

P.S. I'm typing this from an HP dv2600 with an Nvidia 8400m gs, so I'm certain your driver issue can be resolved.

---

### Post by Unix_Slayer on 2008-06-05
> **starcannon said:**
> If you like I'd be willing to VNC in and set it up for you.

PM me if interested.

P.S. I'm typing this from an HP dv2600 with an Nvidia 8400m gs, so I'm certain your driver issue can be resolved.

**See Post ==>** [http://ubuntuforums.org/showthread.php?p=5123669#post5123669]("http://ubuntuforums.org/showthread.php?p=5123669#post5123669")

---

### Post by w1nD on 2008-06-05
> **hotweiss said:**
> OK, I finally installed the new Nvidia drivers using these steps:

0. sudo apt-get remove nvidia*
1. Ctrl-Alt-F1
2. sudo /etc/init.d/gdm stop
3. sudo su
4. sh ./NVIDIA-Linux-x86-173.14.05-pkg1.run
5. go through all the prompts
6. restart

I also found an interesting thread about the new drivers:
[http://www.nvnews.net/vbulletin/showthread.php?t=113919](http://www.nvnews.net/vbulletin/showthread.php?t=113919)

Using the following command should speed up applications like Firefox:



BTW, these drivers are a big improvement.

I followed your steps, but when I login to Ubuntu, I get a white blank screen. Any solution to this? Thanks!

---

### Post by Unix_Slayer on 2008-06-06
> **w1nD said:**
> I followed your steps, but when I login to Ubuntu, I get a white blank screen. Any solution to this? Thanks!

Did you follow my thread, or this one?


My thread ==> [http://http://ubuntuforums.org/showthread.php?t=819043]("http://http://ubuntuforums.org/showthread.php?t=819043")

---

### Post by tekniche on 2008-06-07
> **Unix_Slayer said:**
> Did you follow my thread, or this one?


My thread ==> [http://http://ubuntuforums.org/showthread.php?t=819043]("http://http://ubuntuforums.org/showthread.php?t=819043")

I have tried pretty much everything possible to get the 8400gs to work on the most recent kernel with the most recent drivers but I am still running at 800x600. Which really sucks. Someone help! PLEEEEEAAASSSEEE!!!!!

---

### Post by Unix_Slayer on 2008-06-07
> **tekniche said:**
> I have tried pretty much everything possible to get the 8400gs to work on the most recent kernel with the most recent drivers but I am still running at 800x600. Which really sucks. Someone help! PLEEEEEAAASSSEEE!!!!!

Type in term window:

```
cat /etc/X11/xorg.conf
```

Copy and Paste it to me up here.

---

### Post by Yudraciell on 2008-06-25
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by w1nD on 2008-07-15
> **Unix_Slayer said:**
> Did you follow my thread, or this one?


My thread ==> [http://http://ubuntuforums.org/showthread.php?t=819043]("http://http://ubuntuforums.org/showthread.php?t=819043")

Yeah, I did.

The installation is a success, but after I log in, I get a white screen. Any help on that? Thanks :)

---

### Post by hankypank on 2008-07-22
Hello all
This is my first post on this forum  I am new to linux and just installed ubuntu. Like you I had the problem with screen resolution until I remembered reading this article some time back. So I searched for it so I will post the link here it might help you it certainly helped me.

[http://distrowatch.com/weekly.php?issue=20070903#feature](http://distrowatch.com/weekly.php?issue=20070903#feature)

Good luck hankypank:)

---

### Post by terry_gardener on 2008-07-22
you xorg doesn't seem to look right. 

for example i have the 7900 gs and it looks like this. 

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Tue Mar  4 20:24:34 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Philips PHL 20PF5320"
    HorizSync       31.0 - 60.0
    VertRefresh     47.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7900 GS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1024x768_70 +0+0; DFP: 1024x768 +0+0"
EndSection

---

