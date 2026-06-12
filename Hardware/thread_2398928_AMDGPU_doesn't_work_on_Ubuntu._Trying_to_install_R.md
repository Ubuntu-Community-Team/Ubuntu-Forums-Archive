---
title: "AMDGPU doesn't work on Ubuntu. Trying to install Radeon RX 550."
date: 2018-08-19
forum: Hardware
---

### Post by skiline11 on 2018-08-19
Hi. My old GPU : Radeon HD6770 broke down, and I bought a new graphic card, Radeon RX 550, because it is cheap card, good enough for multiscreen programming. I remember, that installing Ubuntu with HD6770 was pretty easy. Simply plugged in and work out of the box without installing drivers on ubuntu. Only on windows I had to install drivers from attached cd drive.

This time, it was looking totally different. I plugged card in, and screen didnt show up. In Additional Drivers i didn't show any new drivers to install. I read about that I have to install gpu drivers from [LINK1:]("https://www.amd.com/en/support/graphics/radeon-500-series/radeon-rx-500-series/radeon-rx-550")[www.amd.com/]("http://www.amd.com/")... , but there were a lot of issues with these drivers....

Firstly, I downloaded version for ubuntu 16.04.5 from this website, _because that was the software version which I had_. Next I tried to follow instructions from [LINK2:support.amd.com/...]("https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx") . Commands : 
```

sudo apt update
sudo apt dist-upgrade
sudo reboot

```
- all of them works fine. I made reboot, and after that "dpkg -l amdgpu-pro" show that there is no drivers installed.

So I downloaded drivers from LINK1 , extract files and run :
```
sudo ./amdgpu-pro-install
``` Almost everything went fine except few errors "W: Possible missing firmware /lib/firmware/i915/* and /lib/firmware/amdgpu/vegam_*" , but I read its OK.

Then "sudo reboot" and I hope then it will work. But unfortunnately I get errors :
"The system is running in low-graphic mode. Your screen, grapic card and input device settings could not be detected correctly. You will need to configure these yourself." I chose "exit to console" and went to terminal.

Going through amd tutorial from LINK2, I show groups. There wasn't video in it so I run ```
sudo usermod -a -G video $LOGNAME
``` After reboot I got again error : "The system is running in low-graphic mode..."

I chose then "Reconfigure graphics -> Use default (generic) configuration" . Then in groups, the video showed up. Moreover, when I run ```
dpkg -l amdgpu-pro
``` , finally I saw my amdgpu-pro drivers in it. It looks like this :

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinsta-required (Status, Err: uppercase=bad)
||/ Name          Version       Architecture   Description
+++-=============================
il  amdgpu-pro    18.30-633530  amd64          Meta package to install amdgpu Pro components
```

But after reboot I still get "The system is running in low-graphic mode ..."

I tried also to reinstall ubuntu desktop with command : ```
sudo apt-get install --reinstall ubuntu-desktop
reboot
``` but it didnt change anything. Somewhere I find also to reinstall gdm , to make X display manager working. But after ```
sudo apt-get install gdm
--> and choosing gdm3
sudo service gdm start
```, the displayed screen was destroyed and it's blinking all the time and sometimes it shows error : "stopping user manager for uid 121"....


I tried also with another ubuntu distributions like 18.04 and 17.04, and all of them shows errors in some of points of the installation , for example frozing with running
```

sudo apt dist-upgrade
 or
sudo ./amdgpu-pro-install

```
Considering that I didnt have to do anything with my previous graphic card and it was just simple as plug and play, it is very disappointed to me, what amd did with its drivers.

I can return this card and buy new one, if there will not be chance to make it work. Should I consider nvidia gpu's over amd next time? I will read more about it.

I would be grateful if someone would help me.

---

### Post by P-I H on 2018-08-19
There are two choices
- use Ubuntu 16.04 LTS with AMDGPU-PRO
How to install is found here: [https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Driver-for-Linux-Release-Notes.aspx](https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Driver-for-Linux-Release-Notes.aspx)
- use Ubuntu 18.04 LTS with AMDGPU DC. In this case you don't need to install any driver.
The AMDGPU DC driver requires linux kernel 4.15, which is used in Ubuntu 18.04
Some information about Ubuntu and Linux kernels
[https://wiki.ubuntu.com/Kernel/Support](https://wiki.ubuntu.com/Kernel/Support)

---

### Post by skiline11 on 2018-08-19
I am still trying on Ubuntu 16.04 LTS, and as I see again, Drivers Version 17.40 packages can't be extracted and file amdgpu-pro-17.40-*** show that there is data file in it. I had this issue previously and I skipped then to 18.30 version, which I was able to install, as you can see what dpkg showed previously. Now I found [another source]("https://askubuntu.com/questions/975277/cannot-extract-amdgpu-tar-xz") of driver in 17.40 version and install it as it is in tutorial. 

After reboot it still showed error : "The system is running in low-graphic mode...". Then I added video to groups and after reboot it still showed this error. In terminal it stopped on "Started Update UTMP about System Boot about System Boot/Shutdown". I found out to use "apt-get -f install" and after that it still showed "low-graphic mode" error and in "console login" it stopped on "Reached target System Time Synchronized". I will try to fix it tomorrow after work.

---

### Post by skiline11 on 2018-08-24
After many bootloops and reinstalling OS, I figured out how to get closer to solve the problem on Ubuntu 16.04 LTS. Firstly I installed 4.13.12 kernel version for ubuntu 16.04 lts. Next, I installed amdgu-pro drivers in version 16.60-379184, with --compute flag. Then I added video to groups using "sudo usermod -a -G video $LOGNAME" command. Then I saw that :
1) "dpkg -l amdgpu-pro" shows "amdgpu-pro" with description "Meta package to install amdgpu Pro"
2) "lspci -k | grep -EA3 'VGA|Display' shows two compatible controllers: Intel Corporation 82G33/G31 (which is gpu integrated with the motherboard), and Advanced Media Devices ...[AMD/ATI].... (which is my GPU)
3) sudo lshw -C display | grep "driver" show : (configuration: driver=amdgpu latency=0) and (configuration: driver=i915 and latency=0)

Unfortunately, "xrandr --listproviders" command show only one (INTEL) provider. And after loading OS, the screen connected to the motherboard display everything correct, but screen which is connected to GPU(rx550) show only ubuntu logo with bootlooped loading dots. Fortunately, it is not freezing at all, but it still doesn't show the expected image.

---

### Post by wildmanne39 on 2018-08-24
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by skiline11 on 2018-08-25
I'm sorry, I accidentally had to change it and I did not notice it.

---

### Post by skiline11 on 2018-08-26
The problem was that I started pc with one display connected to the motherboard, and another to the GPU. I had "Onboard VGA" enabled in bios, so in Windows, I could see the image from both displays. Unfortunately, Ubuntu had a problem with that combination and show image only from MoBo. When I unplugged one screen from the motherboard, the image from GPU showed up on Ubuntu. And as I tested it out, it works at least on Ubuntu 16.04 and 18.04 without installing any additionals drivers.  I only marked out to "Install third-party software for graphics and Wi-Fi hardware, Flash, MP3 and other media" during installation.

---

### Post by kwalker332 on 2019-03-06
I'm new to Ubuntu, ie poor with terminology and cmnd line.
Running Ubuntu 18.04 on Lubin i7 7700 with a 
[TABLE]
[TR]
[TD]SAPPHIRE Radeon RX 550 DirectX 12 11268-01CPO 4GB 128-Bit GDDR5 Video Card[/TD]
[/TR]
[/TABLE]

Currently, things are okay but not great with amdgpu drivers which I think are open source.  [FONT=Arial]I am having video issues w/ default movie player as well as cheese the webcam app. [/FONT][https://ubuntuforums.org/showthread.php?t=1764741](https://ubuntuforums.org/showthread.php?t=1764741)[FONT=Arial] I don't have the color correction option available which I'm assuming is from having the wrong video driver. I know vlc works but this computer is almost exclusively for video editing and sharing so I need it to not have gaps in functionality. 
[/FONT][FONT=Arial]
root@siren-HP-Pavilion-Desktop-PC-570-p0xx:/home/siren# lshw -c video[/FONT]
[FONT=Arial]  *-display                 [/FONT]
[FONT=Arial]       description: VGA compatible controller[/FONT]
[FONT=Arial]       product: Lexa PRO [Radeon RX 550/550X][/FONT]
[FONT=Arial]       vendor: Advanced Micro Devices, Inc. [AMD/ATI][/FONT]
[FONT=Arial]       physical id: 0[/FONT]
[FONT=Arial]       bus info: pci@0000:01:00.0[/FONT]
[FONT=Arial]       version: c7[/FONT]
[FONT=Arial]       width: 64 bits[/FONT]
[FONT=Arial]       clock: 33MHz[/FONT]
[FONT=Arial]       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom[/FONT]
[FONT=Arial]       configuration: driver=amdgpu latency=0[/FONT]
[FONT=Arial]       resources: irq:130 memory:c0000000-cfffffff memory:d0000000-d01fffff ioport:e000(size=256) memory:df300000-df33ffff memory:c0000-dffff[/FONT]
[FONT=Arial]root@siren-HP-Pavilion-Desktop-PC-570-p0xx:/home/siren# [/FONT]

I cannot play games that I could with the integrated intel graphics though so I'm trying to follow this guide to install proprietary drivers. [https://amdgpu-install.readthedocs.io/en/latest/](https://amdgpu-install.readthedocs.io/en/latest/)

I have tried installing several times requiring wipe/reinstall of ubuntu. I need help understanding my system's current state as well as where to go from here without bricking my os any more times.  Are dedicated graphics active? Do integrated cards work with dedicated or should it only be dedicated? 

I checked the box to install proprietary drivers when fresh installing this but graphics are clearly not right.

---

