---
title: "ATI Drivers?"
date: 2008-11-12
forum: General Help
---

### Post by Quarkrad on 2008-11-12
Just installed 8.10 - am newbie.  I have a r200 type ATI card (all in wonder 8500DV)  - I do not use all he functionality, just want basic graphics.  how do I get a selection of aTI drivers to pick from within system, Admin, Hardware Drivers?   At the moment if I launch 'Hardware Drivers' it is empty and states   '...no propriety drivers are in use on this system...'  
I understand I have to download something to populate 'Hardware Drivers' - but what from where?  At the moment if I run:

sudo nano /etc/X11/xorg.conf

then /etc/X11/xorg.conf tells me:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"

I believe I'm running a standard VGA driver instead of the ATI one.  Any advise greatly appreciated.

---

### Post by binbash on 2008-11-12
sudo apt-get install build-essential xorg-driver-fglrx

sudo aticonfig --initial

---

### Post by Quarkrad on 2008-11-12
Thanks for quick reply.  Followed instruction but after second line/code I got this: 

dad@dad-hp:~$ sudo aticonfig --initial
Uninitialised file found, configuring.
Segmentation fault


When I put in your first instruction it all seemed to load OK - the last few lines reads:

Processing triggers for man-db ...
Setting up dpkg-dev (1.14.20ubuntu6) ...
Setting up libstdc++6-4.3-dev (4.3.2-1ubuntu11) ...
Setting up g++-4.3 (4.3.2-1ubuntu11) ...
Setting up g++ (4:4.3.1-1ubuntu2) ...

Setting up build-essential (11.4) ...

Should I have waited longer before inputting sudo aticonfig --initial?

Many thanks.

---

### Post by binbash on 2008-11-12
after sudo apt-get install build-essential xorg-driver-fglrx this command

you will give sudo aticonfig --initial AND THEN reboot your pc.If you did this and get this output : 

dad@dad-hp:~$ sudo aticonfig --initial
Uninitialised file found, configuring.
Segmentation fault

This is a software error and we cant do anything to that.Instead of aticonfig 

Section "Device"
Identifier "Configured Video Device"
Driver "vesa"

You can change vesa to fglrx .It will do the trick.

---

### Post by Quarkrad on 2008-11-12
Ok - followed your instructions and got the text:

dad@dad-hp:~$ sudo aticonfig --initial
Uninitialised file found, configuring.
Segmentation fault

so I tried editing the **Vesa** entry in the xorg.conf fle.   This is where I went wrong - how do I do this?  I navigated to:

/etc/X11/xorg.conf    opened the file and took out Vesa and put in fglrx.  When I closed the file it said:

**Could not save the file /etc/X11/xorg.conf. You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again.**

Sorry to be a pain - only been with Linux/Ubuntu for a few weeks.

---

### Post by b0b138 on 2008-11-12
Since its a system file it has to opened with sudo/gksudo

open a command line and enter gksudo gedit /etc/X11/xorg.conf

---

### Post by Neo_The_User on 2008-11-12
I always build my own deb packages when installing the ati drivers. If you want to do it the "ubuntu way" then just type this in after installing the xorg fglrx driver. 

```

sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

```

Ignore segmentation fault. Just restart.

If it still won't use the fglrx driver, then type in

```

sudo gedit /etc/X11/xorg.conf

```

When you see something like

```

Section "Device"
	[...]
	Driver		"vesa"
	[...]
EndSection

```

change vesa to fglrx.

---

### Post by Quarkrad on 2008-11-13
Thank you very much - followed advice and indeed changed xorg.conf so that it read fglrx.  Saved the file OK.

Rebooted PC but a splash screen came up stating that:

 **Ubuntu is running in low graphics mode.  (EE) No devices detected.**

Got to the desktop and had a look in System, Admin, Hardware Drivers.  It is still empty, nothing (driver types) to select.

I had  a look in xorg.conf for the video device and it now states:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fglrx"

So I have moved forward in that xorg is now 'seeing?' the fglrx driver but I'm still running in low graphics mode.  Not sure what to do now - sorry.

---

### Post by Quarkrad on 2008-11-13
If I run aticonfig --initial in terminal I get a Segmentation Fault response.

Reading the text file it suggests:

1. Setting up fglrx for the first time.
       Single head :    aticonfig --initial --input=/etc/X11/xorg.conf
 
when I run this command, again, all I get is the Segmentation Fault.

However, if I run **aticonfig --initial=check** then I get:

dad@dad-hp:~$ aticonfig --initial=check
Check: Found fglrx section.

so something is seeing fglrx.

---

### Post by engtg on 2008-11-18
I also upgrade to 8.10 also have the same problem as you.  I tried ever thing I can find on googling and this forum.  Nothing works.

---

### Post by Yellow Pasque on 2008-11-18
fglrx will not work on cards older than the Radeon 9500. Make sure you get rid of all the fglrx stuff by purging it out.
```
sudo dpkg --purge xorg-driver-fglrx
```

---

### Post by engtg on 2008-11-18
Temüjin-- I tried what you said and got rid of all the fglrx stuff by purging it.
And changed by Driver to vesa
Section "Device"

	Identifier     	"aticonfig-Device[0]"

	Driver		"vesa"

	#Driver	"fglrx"

	#Driver	"nvidia"
It worked I am no longer getting the error (EE) No Devices Detected at startup.  My problem is solved
Thank You Temüjin

---

### Post by terribletrouble on 2008-11-18
I can tell you one thing, I will never buy a machine with an ATI card in it again. Linux has been a nightmare with all ATI cards.

On the other hand, NVidia & Intel have been as easy as pie.

I heard that ATI did not give the open source community access to their libs, so everything has to be reverse engineered. They should maintain their partnership with M$.

---

### Post by Yellow Pasque on 2008-11-18
> I heard that ATI did not give the open source community access to their libs, so everything has to be reverse engineered. They should maintain their partnership with M$
This is a very ignorant/outdated/overly simplifed view of things, if it's not an outright troll. Nvidia is the corporate entity that has contributed nothing to the open source world.  At least since AMD has obtained ATI, they've put money/resources into developing their open source radeonhd driver. 

AMD has made great progress in the past year. About a year ago, XGL was required to run Compiz. Now, it runs smoothly with on my X300SE and 690G board with Xorg DRI.

I also have to give props to Intel (especially Keith Packard) for improving the X infrastructure.

Nvidia? They still use all of their own proprietary/binary stuff.

---

### Post by Mr_JMM on 2008-11-18
Temüjin: Well said. Couldn't have put it better.

I use ATI cards and don't have a problem. I don't have much against other brands it's just that I made a choice years ago and have stuck with it.

The problem here is that we have yet another age old "it must be cr** because it doesn't work *on my machine* so they're cr** and their products are cr**". It does get so tiresome.

Let's stick to helping out the OP.

Like I said, I have no problem with ATI cards so it can't just be the card that's an issue. Stick with it and we'll work out the solution.

---

### Post by terribletrouble on 2008-11-18
You guys can say what you want, my _current_ ATI trouble area, is an IBM Thinkpad, T42P, with an ATI RV350 -- aka Mobility Radeon 9600 M10 card in it.

With the latest Intrepid Kubuntu, and the laptop screen (LVDS) and an external 22" (1680x1050) monitor attached to the VGA screen, I can get the install to complete, after the reboot, it boots up, I get to the login screen, and about 10 seconds later, lockup. It requires a cold boot to get going again to the same point where it freezes. Hardy was fine, but with a massively tweaked xorg.conf file. I have been messing with adding XAA options and the like to the conf file, and when I do that, I can get it to boot, but the display is so sluggish - it is unusable.

Now, the T42 is not an ancient machine, it runs very well and has done so for a while.

When I compare this machine, to my other laptop, with Intel graphics on-board, or to my mythtv-backend server with nvidia, or my mythtv-frontend with a 512Mb nvidia, the other machines run like a dream. On hardy, I had to use envyng to get things running, even the T42, now with Intrepid, envyng does install, but I think it just complicates matters (I am not actually sure if it is a supported app?).

Back to the days, when I was running Suse, 7.1, the ATI graphics card I had then - had troubles.

Call me ignorant or outdated, I have been burned one time too many, as I actually cannot seem to run any flavour of Intrepid Ubuntu on this machine now, and am about to see if the likes of Fedora will run on it.

Oh, and since you mentioned compiz, not a chance on the T42.

Clearly, you may know something I do not, regarding the source code contributions of ATI, however these contributions do not seem to be hitting the main stream!

---

### Post by Marius Derekus on 2008-11-18
If you are having trouble with any ATI cards, try this link [http://ubuntuforums.org/showthread.php?t=986559](http://ubuntuforums.org/showthread.php?t=986559)

---

### Post by terribletrouble on 2008-11-18
Thanks!

I went to the site, ready to eat my own words, and apologize for bad-mouthing ATI. 

I downloaded the driver for the Mobility 9600, ran it, rebooted, and am now at the text login screen. No X!

I login, and run```
sudo aticonfig --initial
``` and I get:
```

Uninitialised file found, configuring.
Segmentation fault

```

of course when this is finished, it has added nothing to /etc/X11/xorg.conf.

I am on the wiki site, and reading away....

---

### Post by arosboro on 2008-12-14
I have an ati 9700 pro and I'm getting the same seg fault.  I manually edited the xorg config, but when I reboot I get the following:

#tail /var/log/Xorg.0.log.old
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.55.2
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.552                    
(II) ATI Proprietary Linux Driver Build Date: Oct 28 2008 21:22:33
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 4.1
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found

# modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.27-9-generic/updates/dkms/fglrx.ko): Cannot allocate memory

# tail /var/log/messages
Dec 14 15:32:15 kernel: [  710.921544] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Dec 14 15:32:15 kernel: [  710.983664] [fglrx] Maximum main memory to use for locked dma buffers: 2893 MBytes.


I've been following [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide) as well.

---

### Post by fmb on 2008-12-14
From what I can tell, the driver is either already loaded, or there is another that performs his functionality. Thats why modprobing won't work here.

---

### Post by arosboro on 2008-12-14
I will have to re-install the driver, reboot and get the output of lsmod and dmesg.  

From Xorg.0.log.old:
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found

# lspci | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9700 Pro] (Secondary)

It looks like the second vga port on the card is what isn't being recognized.

I'm also following the issue w/ ati drivers here [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408)

---

### Post by volchara on 2008-12-27
Bump!!!

---

### Post by nightfright on 2009-01-10
I'm also having problems with my newly installed Ubuntu 8.10. 
My notebook (Asus) has a Radeon Mobility 9700 GPU but apparently it wasn't properly detected. An error pops up when X starts saying that the hardware hasn't been configured and that I have to do it by myself.
Since I'm very new to Linux, I don't know how to do that :( I tried to download and install the ATI Radeon Mobility drivers from AMD but they didn't install (I have the Catalyst tool on the applications menu but it doesn't work).
The display is now configured at 800x600 basic resolution, which is not the native resolution of the LCD screen so it's awful to watch, no to mention that there's no hardware acceleration. I hope that some expert here can help me with the ATI drivers setup / configuration.
Please help :)
This is my current xorg.conf file:

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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

---

### Post by redilyn on 2009-01-10
Why not do it the easy way if all you want to do is install the ati binary driver?

```

sudo apt-get install envyng-gtk

```

Then 

```

envyng -g

```

When envy launches choose install the ati driver automatically.

Should get you working without much effort.

Cheers

---

### Post by nightfright on 2009-01-10
Thanks. I tried and apparently it downloaded and installed fine but nothing has changed. The graphic environment still loads in low-res basic mode :(
I also tried to install the ATI drivers from the command line but something seems to go wrong. This is the fglrx-install log:

Creating symlink /var/lib/dkms/fglrx/8.561/source ->
                 /usr/src/fglrx-8.561

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
pushd /var/lib/dkms/fglrx/8.561/build; sh make.sh --nohints; popd.......
cleaning build area....

DKMS: build Completed.
Running module version sanity check.
[Error] Kernel Module : Failed to install fglrx-8.561 using DKMS
[Error] Kernel Module : Removing fglrx-8.561 from DKMS

---

### Post by nightfright on 2009-01-10
By the way, "envyng -g" didn't work. It returns this error: "you need to provide a parameter" and then follows a list of paramaters. "-g" is listed as "not yet available".

---

### Post by redilyn on 2009-01-10
Strange, I'm running hardy so I can't say how well it works in interpid of what options are available.

This is what is returned if you run just envyng in hardy

```

xxxx@xxxxxxxdesktop:~$ envyng
ERROR: you need to provide a parameter:
   "-t" for the textual interface
   "-g" for the GTK frontend
   "-k" for the QT4 frontend
   "--uninstall-all" to completely remove what EnvyNG has done

```

Also I'm afraid I don't know what to tell you about the error while trying to install the driver. Envy has always just worked when I've used it.

---

### Post by utkjamie on 2009-01-15
I've got an ATI Radeon RV250 Mobility FireGL 9000 video card and I've had zero luck switching to the binary drivers. My most recent attempt with the xorg-driver-fglrx caused Ubuntu to give me the "low graphics mode" warning. I've tried other methods over the past few months without any luck.

My goal is to get TV-out working. After a great deal of work, I finally got this working under Gutsy and it continued to work until I upgraded to Intrepid. Not expecting that someone let a bug into the release version of Intrepid, I did what I normally do to switch to TV-out mode and it locked up my computer. Rebooting left with me a series of "missing inode errors" -- corrupted data.

So, I've had to boot into Windows for the sole purpose of using TV-out because Intrepid broke something that had been working. It's extremely frustrating, especially since I keep hearing that the binary drivers will fix the problem and yet I haven't been able to find a way to get the binary drivers to actually work.

---

