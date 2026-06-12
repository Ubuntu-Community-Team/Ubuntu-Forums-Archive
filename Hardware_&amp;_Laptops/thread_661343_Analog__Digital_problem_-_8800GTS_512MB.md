---
title: "Analog / Digital problem - 8800GTS 512MB"
date: 2008-01-07
forum: Hardware &amp; Laptops
---

### Post by bldzr on 2008-01-07
Hi there =)

I'd like to start with apologizing for the somewhat confusing title, but I couldn't really think of anything more precise that would suit my specific problem. This is something that makes the problem hard to google, and I'd be really grateful for suggestions about how to specify my problem in a better way.

I just upgraded from a NVIDIA 7600GT to a [NVIDIA 8800GTS]("http://asus.com/products.aspx?l1=2&l2=6&l3=442&l4=0&model=2003&modelmenu=1") (512MB/N92), something which made me really happy, at least until I installed it and tried to start Kubuntu. After the message about the kernel loading, my [monitor]("http://www.samsung.com/us/consumer/detail/detail.do?group=computersperipherals&type=monitors&subtype=lcd&model_cd=LS22PEBSFV/XAA") starts switching between analog/digital mode before it decides to enter standby-mode. At first, I thought the problems might have something to do with using the DVI-cable, but trying with a VGA-cable didn't help either.
Trying to get into a TTY login screen (ctrl+alt+F1) didn't do anything, so I decided to try with the Live-DVD in "regular" as well as 'Safe Graphics Mode' (with all possible setups using both DVI and VGA-cables on both outputs on the graphics card).

There are no problems using windows (more than the ones already there by default), but that doesn't help me much, I feel like a beached whale without my real OS :(

I'm really stuck on this and I can't seem to get much further on my own, so I'd be most grateful for all the help I can get from the community. I've listed all the relevant information I can think of, if something else is needed to further investigate this problem - please tell me and I'll look it up and post it  ASAP :)


//bldzr


System specs (tell me if further information is needed):

OS: Kubuntu Gutsy 7.10 / Windows XP Professional
Motherboard: Gigabyte GA-P35-DS4 (Intel P35 chipset)
CPU: Intel Core 2 Duo E6750
RAM: 2GB DDR2 6400
Monitor: [Samsung 2232BW]("http://www.samsung.com/us/consumer/detail/detail.do?group=computersperipherals&type=monitors&subtype=lcd&model_cd=LS22PEBSFV/XAA")
Graphics card: [NVIDIA 8800GTS (512MB/N92)]("http://asus.com/products.aspx?l1=2&l2=6&l3=442&l4=0&model=2003&modelmenu=1")

---

### Post by bldzr on 2008-01-08
With the guidance and invaluable help from some nice people in the swedish support channel #Ubuntu-SE (thanks again Yaroze and johanbr) I managed to solve my problem, and since other people might have similar issues I thought I'd contribute by explaining how it was done. Since I'm far from an expert I'd appreciate feedback/corrections from more experienced users (so that we'll avoid that 'blind leading the blind'-situation) :)


Start by booting into recovery mode and edit* /boot/grub/menu.lst* ( *'sudo nano /boot/grub/menu.lst'* ). Scroll down to the section listing your standard boot option, in my case it looks like this:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c59d9bcc-73f8-40b8-aa6e-591452e958d8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

Now edit the 'kernel' line so that it looks like this (removing the 'quiet' and 'splash' options).

```
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c59d9bcc-73f8-40b8-aa6e-591452e958d8 ro
```

Reboot your system, you will now be able to login.

Install [envy]("http://albertomilone.com/nvidia_scripts1.html")
```

sudo apt-get install envy
```

Start envy, and follow the instructions (should be self-explanatory)

```
envy -t
```

Remove and clean your system of the previous drivers, then choose the option to manually install the nvidia driver (envy does not currently detect the new 8800GTS). When asked to reboot, choose yes. Your system should function properly now, with two exceptions.

1. There's currently a bug (#379270) in the nvidia driver (169.07), causing the fan of some nvidia cards (such as the 8800GTS 512MB) to run at 100% speed, which is indeed noisy. You can solve this problem by installing the CVS version of [nvclock]("http://www.linuxhardware.org/**nvclock**/"), which is discussed in the following [**forum thread**]("http://www.nvnews.net/vbulletin/showthread.php?t=104713") at [nvnews.net]("http://www.nvnews.net").
After doing a bit of googling, I found [**this thread**]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=585189") where a nice ubuntu user posted a script which will download and compile the CVS-version of nvclock for you. The binary is placed in your $HOME ( */home/your_user* ) by default. I usually place binarys/scripts in my *'/home/user/bin'* to keep things tidy and organized.


Get and compile the CVS-version of nvclock, the most simple solution would be to use [**Tux0r's script**]("http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4068888&postcount=5")

Start your favorite terminal and follow these steps:

```
cd
mkdir bin
mv nvclock bin/

```

Now we'll create a simple little bash script so that nvclock will run automatically with the preferred settings on startup.

```
nano /home/your_user/bin/nvclockscript
```

Paste the following into the file, and save it 

(**NOTE**: This works great for me and my particular model of the 8800GTS (N92). Since nvclock controls the fan speed of your graphics card, you should investigate which settings are suitable for your specific card, so that you won't risk damaging your hardware. Certain models tend to get very hot, do this at your own risk!).

```

#!/bin/bash

/path/to/nvclock -f -F auto


```

Make the script executable:
```
chmod +x /home/your_user/bin/nvclockscript
```

To run this script on startup, do the following:

In Gnome:
Add it to startup programs in System > Preferences > Sessions.

In KDE:
Create a symlink to the script in your* /home/your_user/.kde/Autostart*

```
cd /home/your_user/.kde/Autostart

ln -s /home/your_user/bin/nvclockscript nvclockscript
```



2. The strange behaviour with the monitor switching between analog/digital (...and eventually going into standby-mode) is still there if you try booting with the 'splash' option enabled. This isn't really a huge problem, you'll get back on track once gdm/kdm starts, but if someone happens to know the solution for this, it'd be great if you posted the solution =)

---

