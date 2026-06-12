---
title: "Howto Sony Vaio VPC-Z2 on Precise"
date: 2012-09-09
forum: Hardware
---

### Post by dothedog on 2012-09-09
Howto Ubuntu Precise with Vaio VPC-Z2

This is an update to [http://ubuntuforums.org/showthread.php?t=1850544](http://ubuntuforums.org/showthread.php?t=1850544)

The big update for this is the Power Media Doc with the AMD 6650 now works mostly.

First thing to do is make sure you are all updated. Check update manager. Check and update all.

There was a pretty bad power regression to 3.5 for the sandy bridge. This has mainly been solved as of 3.6-rc4 and on. There were also some issues with fuse (couldn't write to ntfs). I will write this based on the latest as of this writing 3.6-rc5.

Download the source for 3.6-rc5 from kernel.org from here: [http://www.kernel.org/pub/linux/kernel/v3.0/testing/linux-3.6-rc5.tar.bz2](http://www.kernel.org/pub/linux/kernel/v3.0/testing/linux-3.6-rc5.tar.bz2)

in terminal copy it to /usr/src
```
sudo cp ~/Downloads/linux-3.6-rc5.tar.bz2 /usr/src/
```

unzip
```
cd /usr/src
sudo tar -xjvf linux-3.6-rc5.tar.bz2
```

create a COMPILE script and save it to /usr/src/COMPILE
```
#!/bin/bash
# COMPILE

sourcedir=linux-3.6-rc5
ver=01
cd $sourcedir
export CONCURRENCY_LEVEL=3

nohup /usr/bin/time -o TIME fakeroot make-kpkg \
  --initrd --append-to-version=-$ver \
  kernel_image kernel_headers >& OUTPUT &

```

Notes: sourcedir should be the  3.6-rc5 directory, ver= can be any number but it will append it to the end of the kernel name, CONCURRENCY_LEVEL should be number of cores + 1 (Not sure if that makes a difference though) 

save the script as COMPILE in the /usr/src/ directory and make it executable.
```
cd /usr/src
 sudo chmod +x COMPILE
```
I don't believe that you need to patch anything to get the PMD working or fix the power regression. So just make sure you have all your all your packages for compiling your kernel.

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install fakeroot kernel-wedge makedumpfile libncurses5-dev libqt3-mt-dev build-essential crash kexec-tools git-core  libelf-dev asciidoc binutils-dev
sudo apt-get build-dep linux
```

Run the COMPILE script
```

cd /usr/src/
sudo ./COMPILE
```
you can check the progress by
```
tail -f /usr/src/linux-3.6-rc5/OUTPUT
```
when it completes you can check the compile time by:
```
cat linux-3.6-rc5/TIME
```
Mine took about 36 minutes shown below: ```
cat TIME 
4872.52user 427.43system 35:51.20elapsed 246%CPU (0avgtext+0avgdata 1911968maxresident)
4559640inputs+27232464outputs (5256major+203660840minor)pagefaults 0swaps
```
In the /usr/src dir you should have two .deb files.
```
--rw-r--r--  1 root     src       8121206 Sep  9 16:03 linux-headers-3.6.0-rc5-01_3.6.0-rc5-01-10.00.Custom_amd64.deb
-rw-r--r--  1 root     src      39926984 Sep  9 16:01 linux-image-3.6.0-rc5-01_3.6.0-rc5-01-10.00.Custom_amd64.deb
```

Install them by 
```
sudo dpkg -i  linux-image-3.6.0-rc5-01_3.6.0-rc5-01-10.00.Custom_amd64.deb
sudo dpkg -i  linux-headers-3.6.0-rc5-01_3.6.0-rc5-01-10.00.Custom_amd64.deb
```

Now we need to add a file to get the new PMD graphics.
```

sudo mkdir -p /etc/X11/xorg.conf.d
sudo nano /etc/X11/xorg.conf.d/60-dualhead.conf
```
Copy this into the file:
```

Section "Device"
    Identifier "radeon"
    Driver "radeon"
    BusID "PCI:22:00:0"
EndSection

Section "Device"
    Identifier "intel"
    Driver "intel"
    BusID "PCI:00:02:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "radeon"
EndSection

Section "Screen"
    Identifier "Screen1"
    Device "intel"
EndSection

#Section "ServerLayout"
#    Identifier "DualHead"
#    Screen "Screen0"
#    Screen "Screen0" RightOf "Screen1"
#    Option "Xinerama" "On"
#EndSection

```

If you uncomment the last section does open an x-session on the laptop but it still needs work. 

now edit the grub line:
sudo nano /etc/default/grub
change your GRUB_CMDLINE_LINUX line, remove the &#8220;nomodeset&#8221; and add the following.
```
GRUB_CMDLINE_LINUX="i915.i915_enable_rc6=1 pcie_aspm=force drm.vblankoffdelay=1  i915.lvds_downclock=1 i915.semaphores=1"
```

*Not sure if all of them are required now but I get an average of about 12-15 Watts

save. 
then do 
```
sudo update-grub
```
now reboot
```
sudo reboot now
```

On reboot You should now have Unity desktop but compiz isn't working on the intel card.  Glxgears is running at about 1,200 fps. Do this to make sure 3d works:
```

$ glxinfo | grep version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL version string: 2.1 Mesa 8.0.2
OpenGL shading language version string: 1.20

$ glxinfo | grep direct
direct rendering: Yes

```
I have compiz working on the AMD graphics on the PMD. If anyone can figure out how to make it work on both, please respond to this thread.

What works:
Proc
Raid-0
Ethernet both on laptop and the PMD
PMD Graphics 
Compiz on PMD Graphics
Clickpad (although still don't get three finger tap for middle click)
Wifi - centrino advanced-n 6230
fn+F3 and fn+F4 work to adjust audio volume
fn+F5 and fn+F6 work to adjust screen brightness 
webcam works ootb
Microphone works ootb
TTY's work (cntrl+alt+F2, etc.)
Suspend works
Haven't tested hibernation
Power Utilization &#8211; Still getting about 12-15 Watts which is a bit high. With 45 Watt hours thats only about 3-3.75 hours. I think this could be better.

What doesn't work.
Hotplug of the PMD. Unfortunately this script [http://ubuntuforums.org/showpost.php?p=12162057&postcount=18](http://ubuntuforums.org/showpost.php?p=12162057&postcount=18) doesn't work with the graphics. So you need to plug in the PMD before you boot and it will work. Good thing the z boots fast ;) 
Fingerprint reader &#8211; It doesn't work that great in Winbloze either.
WWAN &#8211; vick on the [https://lists.launchpad.net/sony-vaio-z-series/](https://lists.launchpad.net/sony-vaio-z-series/) seems to have gotten his to work with qcserial. But I can't seem to get it to work and GobiSerial doesn't compile on 3.6. I actually have it working on the 3.2 kernel so I am keeping that so I can use the WWAN and use the 3.6 when I need the PMD. Luckily I don't have to use them both at the same time very often.

Please post if you have any solutions to the WWAN, improve Power, or Compiz on the intel card.

Rob

---

### Post by MarcoDiMarco on 2012-09-10
Im following your tutorial but couldnt use fakeroot. I've had to install the package named "kernel-package". Otherwise fakeroot reports a error:

```
fakeroot: error in line #: command make-kpkg: command not found
```

Its now compiling. Thanks for your tutorial!

Roberto

---

### Post by MarcoDiMarco on 2012-09-10
Im now trying to safe the file for the PMD but the directory doesnt exist. Can i create the directory or do i need to install some driver before i can create the file ?

Im talking about this part:
```
sudo nano /etc/X11/xorg.conf.d/60-dualhead.conf
```

---

### Post by dothedog on 2012-09-10
Yeah, I just created the directory. I believe it is actually a deprecated method but it works for now. I guess I should add that. 

Rob

---

### Post by MarcoDiMarco on 2012-09-11
Hi,

I've compiled the kernel, did not patched it (just like you said), installed the Kernel, modified GRUB and created 60-dualhead.conf. 

I've rebooted the device with the docking station connected but no luck. 
I noticed that glxinfo doesnt work. What package do i need to install to get that working ?
Did i do anything wrong?

=======================


/etc/default/grub !!! I noticed i didnt had the nomodeset in this file!!!
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="i915.i915_enable_rc6=1 pcie_aspm=force drm.vblankoffdelay=1  i915.lvds_downclock=1 i915.semaphores=1"

```

60-dualhead.conf
```
Section "Device"
    Identifier "radeon"
    Driver "radeon"
    BusID "PCI:22:00:0"
EndSection

Section "Device"
    Identifier "intel"
    Driver "intel"
    BusID "PCI:00:02:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "radeon"
EndSection

Section "Screen"
    Identifier "Screen1"
    Device "intel"
EndSection

#Section "ServerLayout"
#    Identifier "DualHead"
#    Screen "Screen0"
#    Screen "Screen0" RightOf "Screen1"
#    Option "Xinerama" "On"
#EndSection

```

---

### Post by dothedog on 2012-09-11
I believe an 
```
sudo apt-get update
sudo apt-get install mesa-utils
```
will get you glxinfo.

Also you shouldn't need nomodeset anymore. I haven't had it for a few kernel versions.

It's hard to tell what may have gone wrong on your kernel compile. Have you tried booting without the PMD connected? It should work. Also, make sure you don't have radeon blacklisted. I have seen some old guides that told you to do that. It works now.

Rob

---

### Post by MarcoDiMarco on 2012-09-12
> **dothedog said:**
> I believe an 
```
sudo apt-get update
sudo apt-get install mesa-utils
```
will get you glxinfo.

Also you shouldn't need nomodeset anymore. I haven't had it for a few kernel versions.

It's hard to tell what may have gone wrong on your kernel compile. Have you tried booting without the PMD connected? It should work. Also, make sure you don't have radeon blacklisted. I have seen some old guides that told you to do that. It works now.

Rob

Thank you for your response. I will install these packages. 

About the pmd. Did you compiled the kernel with the pmd connected? Or shouldnt this affect the compiling?

---

### Post by dothedog on 2012-09-12
Shouldn't make a difference if it is connected when you compile or not. Just make sure there are no errors in your OUTPUT file. 

Rob

---

### Post by MarcoDiMarco on 2012-09-19
> **dothedog said:**
> Shouldn't make a difference if it is connected when you compile or not. Just make sure there are no errors in your OUTPUT file. 

Rob

Hi,

I just redid everything but still without success.

Just to be sure, the pmd is working, meaning that the Ethernet and USB ports are working as well right? Cause thats how i test it....

Also, how to check if its blacklisted? And if so, how to whitelist it again ?

Thank you so much for your help so far!

** UPDATE **

I recompiled the kernel using the patches from earlier, still without success. I also connected al my external monitors but still nothing. I feel like im missing a part. 

Should I reinstall the system entirely ?

---

### Post by dothedog on 2012-09-26
If you are using 3.6-rc5 or greater you shouldn't need any patches to get the PMD to work. Also, please make sure that you have the PMD attached when you boot. It does not hotplug at this point. And yes, the USB, BR Rom,and Ethernet all should work.

As far as blacklisting goes look in /etc/modprobe.d/
See if in blacklist.conf there is a line that says "blacklist radeon" or if you have a file in there that is called blacklist-radeon or some such. If you have a line in blacklist.conf you can just comment it out by putting a "#" in front of the line. I guess you could do the same if you have a blacklist-radeon file as well.

I'm not sure you need to re-install at this point.

Rob

---

### Post by MarcoDiMarco on 2012-10-02
Hi thanks for your response.

I dont get it. Yesterday I've reinstalled my system, downloaded the 3.6-rc7 kernel from kernel.org, compiled it using "make menuconfig" etc etc and installed it. Only error I've had to deal with was the following:
```
ERROR: "__modver_version_show" [drivers/staging/rts5139/rts5139.ko] undefined!
WARNING: modpost: Found 1 section mismatch(es).
```
I resolved this by disabling that module. Dont think this could be the problem.

Still have no succes.

Could I get a copy of your .config, maybe there are differences within those files which I havent noticed.. 

Sidenote:
I find it very strange that when booting from my usb (live ubuntu version) that the PMD works out of the box... I'm trying to find out the differences between those as well.

---

### Post by MarcoDiMarco on 2012-10-03
Okay im very much confused. Yesterday I compiled the 3.6-rc7 kernel from kernel.org with the config from the live usb (config-3.2.0-23-generic)... I havent changed a thing..still without succes..
This is now really bugging me and I'm afraid that the release of the 3.6 kernel wont even matter for my device ?

---

### Post by dothedog on 2012-10-11
Marco,
Not sure what to tell you. I just compiled the stable 3.6.1 kernel from kernel.org and it is booting etc. just fine. I have not checked to make sure that it works on the PMD but I don't doubt that it will work.  I am attaching my .config file, but I didn't make any changes to it. The .config file is in a .zip format.

Just to confirm, you have a vpc-z2, you are plugging in the PMD prior to boot, you are using the HDMI cable from the PMD to the display? You have added the xorg stuff. Do you get a TTY output on your laptop? Do the network, BD Rom and USB stuff on the PMD work? Because even before we got the display working, the network, BD and USB worked out of the box.

Not sure what else to tell you.

Rob

---

### Post by MarcoDiMarco on 2012-10-13
> **dothedog said:**
> Marco,
Not sure what to tell you. I just compiled the stable 3.6.1 kernel from kernel.org and it is booting etc. just fine. I have not checked to make sure that it works on the PMD but I don't doubt that it will work.  I am attaching my .config file, but I didn't make any changes to it. The .config file is in a .zip format.

Just to confirm, you have a vpc-z2, you are plugging in the PMD prior to boot, you are using the HDMI cable from the PMD to the display? You have added the xorg stuff. Do you get a TTY output on your laptop? Do the network, BD Rom and USB stuff on the PMD work? Because even before we got the display working, the network, BD and USB worked out of the box.

Not sure what else to tell you.

Rob

Thanks for your config, Ill check it tomorrow with my own.

As for your questions:
VPC-Z2: Check.
PMD connected before boot: Check.
Added xorg stuff: check.
HDMI connection: check, I have both ports (hdmi, vga or dvi) connected on the PMD, nothing on my vaio except for the lid screen.
GRUB stuff: check.
Network, BD-ROM and USB stuff working: false. These do not work at all, only when booting from a live usb. After install its all dead, even with the 3.6 kernel....

---

### Post by dothedog on 2012-10-17
Marco,
Man, I really don't know what to tell you at this point. Especially if your usb and ethernet doesn't work on the PMD. That has always worked. Do the usb and the ethernet on the PMD work with the 3.2 kernel for you?

Rob

---

### Post by MarcoDiMarco on 2012-11-23
Okay today i installed the Linux Mint 14 release. Still same problem, when running the live kernel: everything works. When running the installed kernel: nothing works.

Beneath a screenshot as proof that i do have a Vaio Z21 with the question to confirm my model as being able to run the setup as described in this topic:

[IMG]http://puu.sh/1tmTF[/IMG]

I'm really getting desperate about this whole situation.. :(

---

### Post by dothedog on 2012-12-06
Marco,
So what kernel version are you running? Also, have you tried running in Windows? Does the PMD work in Windows ok? Not sure how to help at this point.

Rob

---

### Post by MarcoDiMarco on 2012-12-06
> **dothedog said:**
> Marco,
So what kernel version are you running? Also, have you tried running in Windows? Does the PMD work in Windows ok? Not sure how to help at this point.

Rob

Like i said in my email, i can confirm that the PMD is working on Windows. Seems like a Driver problem but i cannot figure that out. 

The PMD should work with kernel 3.2 and above right?

---

### Post by dothedog on 2012-12-26
Sorry to be so slow on the reply. If you are on 3.2 you will need a couple of patches to get it to work correctly. I would try updating to the 3.6.9 or 3.6.11 that is up on kernel.org. I am currently running 3.6.9 without any problems. I haven't tried the 3.7 yet.

Rob

---

### Post by GeraldNunn on 2012-12-27
I installed kernel 3.6.9 and applied the xorg conf file for dualhead along with the grub changes and now have the PMD working successfully and driving two monitors. A couple of questions as follows:

a. Things seem a little sharper on my HDMI monitor then my DVI monitor being driven by VGA whereas usually it is the opposite with my older laptop. On my older laptop the monitor using VGA was being driven by DVI and not VGA, is this possibly due to VGA being analog and not as good as a digital DVI signal?

b. The laptops internal screen is blank but the backlight is still active, how can I disable the backlight on the internal screen.

c. I'm using the open source radeon drivers, has anyone tested this with the catalyst drivers to see if it works?

---

### Post by GeraldNunn on 2012-12-27
Answering my own questions, to some extent anyway, I found the following:

1. Switched from VGA to an HDMI>DVI cable and the picture is way better

2. Realized the laptop isn't blank, it actually has a TTY output on it and when you do a CTRL-ALT-F2 it opens the terminal on the laptop screen, neat

3. Tried the Catalyst drivers but had no luck with it at all, Ubuntu hangs on boot and I get the following error message:

Dec 27 13:07:11 gnunn-laptop2 kernel: [   11.925204] <3>[fglrx:hal_read_VBIOS] *ERROR* Invalid AMD VBIOS!
Dec 27 13:07:11 gnunn-laptop2 kernel: [   11.925207] <3>[fglrx:hal_init_gpu] *ERROR* Failed to read VBIOS!
Dec 27 13:07:11 gnunn-laptop2 kernel: [   11.925208] <6>[fglrx] device open failed with code -1

---

### Post by MarcoDiMarco on 2013-01-03
> **dothedog said:**
> Sorry to be so slow on the reply. If you are on 3.2 you will need a couple of patches to get it to work correctly. I would try updating to the 3.6.9 or 3.6.11 that is up on kernel.org. I am currently running 3.6.9 without any problems. I haven't tried the 3.7 yet.

Rob

No problem. I just had a big breakthrough! I found out that my bios has been modified and did not contain default settings. I did a factory reset on my bios settings and ques what...the PMD now works!!!
I am going to install the 3.7 kernel now. I find that the PMD keeps running hot (the blower seems to work 100% and it gets really hot!).

Anywaysz, thanks for all the help and patience you have been giving me! I'm nearly there!!

---

### Post by gyhor on 2013-01-11
hi,

did anyone got a triple screen configuration with gnome-shell or unity working (two external screen + internal screen)?
Or does somebody know to config dual screen + tty output on the internal screen?
I would be really convenient to able to use the internal screen for logging output like  here:
[http://mikebeach.org/2011/05/28/ubuntu-real-time-syslog-logging-to-unused-console-tty/](http://mikebeach.org/2011/05/28/ubuntu-real-time-syslog-logging-to-unused-console-tty/)

regards

---

### Post by jboogie000 on 2013-01-11
Firstly thanks a lot i've been waiting to use my PMD for over a year :)

secondly the audio of my z21 outputs through its speakers rather than HDMI. Is there some way I can get audio to output through my HDMI connection? the only output device listed in the settings is onboard speakers.

Also during the setup my my system I made the mistake of not naming my 60-dualhead.conf correctly and well PMD was working fine with exception of the videoout however the HDMI/VGA ports on the laptop outputed video using the ATI video card so I was able to get a 3 monitor setup. But in my pursuit to follow your guide I ended up with two monitors via the pmd and a console that cannot be used without freezing my lightdm session. I'm hoping someone with more xorg knowledge can figure a work around for this...

btw i'm using kernel 3.7.1
--------------
Nevermind i forgot to update-grub after adding radeon.audio=1 as a kernel boot parameter

---

