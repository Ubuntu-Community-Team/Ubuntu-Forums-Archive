---
title: "Won't boot after GeForce GT 240 Installed"
date: 2015-02-24
forum: Hardware
---

### Post by Sam_Agustini on 2015-02-24
Machine is an IBM ThinkCentre A51 3Ghz PIV 2GB RAM, UBUNTU 14.04 LTS. This machine is old but serviceable. Used for browsing internet and as a terminal to Remote Desktop into servers. I thought it'd be worthwhile to upgrade the integrated Intel graphics to a NVIDIA GeForce GT 240 on the one PCIe 16x slot on the MB.

Systems sits on Ubuntu screen unusually long time and then displays a checkered splash screen apparently locked-up. The BIOS detects the card and makes it primary, so once seated I cannot get video from onboard VGA. I previously downloaded the binaries from Nvidia to my downloads folder.

Have searched this forum and Googled, but most of the issues posted are installing Ubuntu on machine with this graphics card, not upgrading to it - I really do not wish to re-install as I just resolved a wireless issue that took some time to get working stable.

I am a newbie to Linux. I like the fact that this machine which would be a rather large paperweight (in the Winders world) can do work and perform well using this OS. Would perform even better if I could get this graphics card working!

---

### Post by oldfred on 2015-02-24
You should be able to boot with nomodeset. And install nVidia driver from Ubuntu repository, not from nVidia. If you install from nVidia, you have to do updates to reinstall nvidia driver into kernel. If from repository or ppa then that is automatic.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

It looks like you can use a legacy driver. Not sure if 340.xx is yet in repository, but newest version less than that should work for your system.
       nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

---

### Post by Sam_Agustini on 2015-03-14
Thank you oldfred. I took a look at those links and dude, like I said, I'm a Linux newbie and frankly, those links weren't very useful {sorry}. But I am not new to PC's and this was obviously a driver issue. Back in the old Windows days (prior to '95), it might have been an IRQ issue as well. So I pulled the card and booted to the on-board VGA. Followed the instructions here add PPA repository and the 304.108 NVIDIA drivers> Shut down, re-install GT 240 card, re-boot. All good now!

[http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/)

---

### Post by sudodus on 2015-03-14
I'm glad you found a solution, that works well for you :KS

Exactly(?) the same card (at least the name and model number are the same) sits in a friend's computer, that I upgraded from XP to Xubuntu today. I installed version 14.04.1 LTS (32-bit), and it worked directly with the built-in driver 'nouveau'. I installed the proprietary nvidia 304 driver from the repository with

```
sudo apt-get install nvidia-304
```

because I wanted some advanced features for playing high-definition video (1920x1080-50p).

Then I received the point version 304.125 (obviously a newer version than yours), and I keep it because it works well.

To make it play high-definition video really well, I installed openbox and mplayer2, and run mplayer2 in an openbox session.

---

