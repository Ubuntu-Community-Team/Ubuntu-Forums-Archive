---
title: "Downgrade Xserver 1.13 to 1.12 in order to install nvidia drivers properly"
date: 2013-03-09
forum: Hardware
---

### Post by patriciosainz on 2013-03-09
[SIZE=3]Hello, this is my first thread and I wanted to share with you my own experience with the frustrating experience about installing NVIDIA drivers in kubuntu. Sorry first of all, my awful english :).
My computer is an intel 2.4 ghz with 1 Gb RAM and NVIDIA GeForce 4 mx 440 AGP 8x all on a Gigabyte 8S648FX motherboard.
1. Its not possible for this NVIDIA Geforce to be installed in Kubuntu 12.10 because NVIDIA-Linux-x86-96.23.43-pkg1.run must be installed in Xserver 1.12 or less and Kubuntu 12.10 has Xserver 1.13 This is the reason that NVIDIA give us:[/SIZE]

Why does NVIDIA not provide RPMs anymore?  A. Not every Linux distribution uses RPM, and NVIDIA wanted a single solution    that would work across all Linux distributions. As indicated in the NVIDIA    Software License, Linux distributions are welcome to repackage and    redistribute the NVIDIA Linux driver in whatever package format they wish.

[SIZE=4][FONT=arial]So I though I should wait (be[SIZE=4]tter sat) N[SIZE=4]vidia up[SIZE=4]dates to new drivers for Xorg 1.13 but I found asking Mr. google how cou[SIZE=4]ld I downgrade to a[SIZE=4] Xorg version [SIZE=4]1.12 that allow me t[SIZE=4]o run my drivers properly[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE] and this was what I found:
Info source[SIZE=4]: ubuntu.info/tag/xorg
'How to install drivers...' There [SIZE=4]you can see h[SIZE=4]ow to downgrade [SIZE=4]Xorg 1.13 to Xorg 1.12[SIZE=4] in this way:
[SIZE=4]sudo add-apt[SIZE=4]-[SIZE=4]repository ppa:makson96/fglrx
sudo apt-get update
su[SIZE=4]do apt-get upgrade
sudo apt-get install fglrx-legacy[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

And then I could install[SIZE=4] al [SIZE=4]least my Nvidia drivers in Kubuntu 12.10 with Xorg 1.12
ctrl+f1
[/SIZE][/SIZE][/SIZE]sudo stop lightdm
sudo sh NVIDIA-Linux-x86-96.[SIZE=4]43.23-pkg1.run
etc
[SIZE=4]I think is too complicated to configure your graphic card in ubuntu and that's[SIZE=4] proba[SIZE=4]bly one of a hundred [SIZE=4]re[SIZE=4]asons [SIZE=4]to make people not to instal[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]l Linux which [SIZE=4]shown me that is much better than microsof[SIZE=4]t windows.
[SIZE=4]So It's a pity if [SIZE=4]Hardware [SIZE=4]Companies [SIZE=4]don[SIZE=4]'t support Linux[SIZE=4], I will continue working and learning [SIZE=4]Linux on my virtual machine Vmware[SIZE=4].[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

[/FONT][/SIZE]

---

### Post by 3WrKB4C on 2013-09-28
Hi, thanks a lot for the suggestion, it worked smoothly for me also under Lubuntu 12.10.
Just a note: my system was running NOUVEAU, so when I run the NVIDIA installer script, it installed a modprobe conf preventing the nouveau from being run upon startup. I had to reboot the system to re-run the installing script. Then sudo stop lightdm does not work anymore, and the correct synthaxis is 
> sudo service lightdm stop
then you can run the installer again with
> [SIZE=2][FONT=arial]sudo sh NVIDIA-Linux-x86-96.43.23-pkg1.run[/FONT][/SIZE]
Thanks again!

---

