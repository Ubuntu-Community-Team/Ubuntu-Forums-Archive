---
title: "Ubuntu 12.04 64 bit stuck on screen resolution 1024x768"
date: 2013-10-15
forum: Hardware
---

### Post by Philip Gray on 2013-10-15
Good evening

Recently I purchased a new PC. I am dual booting with Ubuntu 12.04 64 bit and Windows 7 Ultimate 64 bit. My issue is that in Ubuntu I only have two screen resolutions. Namely 1024x768 and 800x600, whereas in Windows I am on 1280x864. I have been on various forums trying to find posts that may help me out. I found some on this forum, AskUbuntu, Debian, nothing worked. I noticed that in my X11 folder I do not have a xorg.conf file.

One of the suggestions on AskUbuntu was to run 'sudo apt-get install xserver-xorg-video-intel' and if it did not work to run apport-bug xorg.When I rebooted after installing the Intel drivers I had a blank, black screen with no cursor. I then tried to use the recovery option but my terminal prompt kept disappearing. I tried uninstalling the drivers using apt-get remove from the live cd. No luck I eventually reinstalled Ubuntu.

Some of the other suggestions were to create a xorg.conf file. I tried creating a new one. When that did not work I tried modifying the one in my Ubuntu 12.04 32 bit installation. All I got was a blank screen. I downloaded from 01.org and tried to install two these packages but all I got were error messages:
intel-linux-graphics-installer_1.0.1_amd64.deb
intel-linux-graphics-installer_1.0.2-0intel3_amd64.deb

My new PC's hardware is as follows:
Gigabyte GA-B75M-D3H motherboard
INTEL CI5 3330 3.0GHZ 6MB LGA CPU
Intel Ivybridge HD 2500
16GB DDR3 1333 memory
2TB SATA hard drive
1TB SATA hard drive
2x SATA DVD writer
AOpen LCD 17" TFT-LCD monitor aspect ratio 4:3
Model: F2705-12S
Rating: 100-240V~, 50/60Hz 1.0A

I also ran these two commands:
philip@philip-desktop:~$ sudo lspci | grep VGA
[sudo] password for philip: 
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
philip@philip-desktop:~$

philip@philip-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
philip@philip-desktop:~$ 

I also found this on 01.org
Downgrade for Ubuntu 12.04
Get u12.04-downgrade.tar 
Uncompact: $ tar xf u12.04-downgrade.tar 
Roll back by running it: $ sudo sh ./downgrade.sh

I am hesitant to do this as I do n ot know how to undo it. I checked in Synaptic and found that this package has been installed: 
xserver-org-video-intel-lts-quentzal   version 2:2.20.9-0ubuntu2.

I am stumpted and rather frustrated. I will really appreciate any suggestions?

Regards
Philip

---

