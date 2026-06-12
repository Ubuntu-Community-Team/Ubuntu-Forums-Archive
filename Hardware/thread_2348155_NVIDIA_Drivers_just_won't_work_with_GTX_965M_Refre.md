---
title: "NVIDIA Drivers just won't work with GTX 965M Refresh"
date: 2017-01-01
forum: Hardware
---

### Post by conna on 2017-01-01
[COLOR=#111111][FONT=Ubuntu]I'm trying to install the latest NVIDIA drivers for my GTX 965M Refresh on a Skylake board. I run Ubuntu MATE 16.04 with the stock kernel 4.4.0.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I added the graphics-drivers PPA. Now when I select *any* of the NVIDIA drivers under "additional drivers" in system settings, it does install them correctly, but the system won't boot anymore.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I tried 375.26, 370.28 and 367.57 with kernel 4.4.0, 4.4.39 and also 4.8 - same issue with all of them. The system freezes right after selecting a kernel in GRUB (blinking underscore cursor at the left top of the screen where you can type but not run anything) and it doesn't write *anything* to syslog or kern.log that could help me figure out what the issue is about.

I tried the .run files from nvidia.com too with the same result. Of course I also tried manual package installations via apt instead of using the additional drivers manager.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I disabled secure boot in BIOS. I use UEFI mode. I disabled the second onboard video card in the BIOS settings too, so that shouldn't be conflicting. I did purge nvidia-* several times before installing other drivers. I also tried manually setting nomodeset in my GRUB config, but no luck.

I've spent at least 5 hours on this by now and tried every documented suggestion I could find, but nothing seems to work. It's frustrating as hell because Nouveau also doesn't seem to work properly with that card, at least it doesn't detect my external monitor properly. Laptop screen and external monitor both go dark as soon as I plug in the HDMI cable, which is why I want to get the NVIDIA drivers to work in the first place, hoping that they will solve that weird issue.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any ideas how the heck I could debug this or what else I could try? This shouldn't be related to a specific NVIDIA driver version or kernel, because I tried several combinations of those already. What can I do?[/FONT][/COLOR]

---

### Post by oldfred on 2017-01-01
Are you purging previous nVidia driver before installing a new one?
New driver does not totally overwrite old and then you get conflicts and nothing works.

       If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Do not use .run from nVidia. That in essence requires reinstall with every kernel update. 
 

 sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX  

      
 Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices

---

### Post by conna on 2017-01-01
Thank you for your quick response.

> **oldfred said:**
> Are you purging previous nVidia driver before installing a new one?
Yes, I do this each time. I always have to from recovery mode, because the system doesn't boot with any NVIDIA kernel module installed.

> **oldfred said:**
> 
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
I do remove the xorg.conf as well. Actually the deb packages don't run nvidia-xconfig automatically, which means I don't use any xorg.conf at all. Of course I tried generating one with nvidia-xconfig too, but that doesn't help because the system doesn't boot far enough to start X. It doesn't freeze at login screen, but much earlier directly after GRUB selection.

> **oldfred said:**
> Do not use .run from nVidia. That in essence requires reinstall with every kernel update. 
I know. Just tried it once due to lack of alternatives and then removed the kernel I tried it with (looks like nvidia-uninstall script doesn't remove all leftovers - I wasn't able to boot the kernel I tried it with even after running that uninstall script).
 

> **oldfred said:**
> sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX 
I tried all these mentioned methods. All 3 drivers that the ubuntu-drivers tool suggested and also manual apt-get installations (see OP).

> **oldfred said:**
> sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices I already use that PPA (see OP).

---

### Post by oldfred on 2017-01-01
Perhaps similar to this thread?

 Linux: Finally A Real Fix For Optimus Technology For Notebook Computers xorg-xserver 1.19
[https://ubuntuforums.org/showthread.php?t=2329171&page=3](https://ubuntuforums.org/showthread.php?t=2329171&page=3)
bbswitch issues with kernel 4.8 Boot parameter pcie_port_pm=off
Dell XPS 15 9550, gpu is Intel HD 530 + GeForce GTX 960M.
[https://github.com/Bumblebee-Project/bbswitch/issues/140](https://github.com/Bumblebee-Project/bbswitch/issues/140)

---

### Post by conna on 2017-01-01
> **oldfred said:**
> Perhaps similar to this thread?

 Linux: Finally A Real Fix For Optimus Technology For Notebook Computers xorg-xserver 1.19
[https://ubuntuforums.org/showthread.php?t=2329171&page=3](https://ubuntuforums.org/showthread.php?t=2329171&page=3)
bbswitch issues with kernel 4.8 Boot parameter pcie_port_pm=off
Dell XPS 15 9550, gpu is Intel HD 530 + GeForce GTX 960M.
[https://github.com/Bumblebee-Project/bbswitch/issues/140](https://github.com/Bumblebee-Project/bbswitch/issues/140) Could you point me to a particular post? I don't see anyone having issues to boot with the current or previous NVIDIA drivers. Also in BIOS I selected a setting to force the system to always use the NVIDIA card instead of the Intel onboard. If I switch to hybrid mode (which I have disabled, but think the issues you referenced are about - also they are about Xorg 1.19 while I'm on 1.18), it boots fine using the Intel onboard card. I might have to try a different distro and see if I run into the same issue - kinda out of ideas.

---

### Post by oldfred on 2017-01-01
I got the impression from those threads that issues are related to needing newest kernel & Xoorg 1.19. Which should be in 17.04, but not sure if already in it yet or not. My last install of 17.04 was a month ago. You can experiment with 17.04, but realize it is not near final yet.

---

### Post by conna on 2017-01-02
Not that simple unfortunately. The threads you linked are about running the cards in hybrid mode, but I disabled the Intel card in BIOS, which means only the NVIDIA one is active (therefore I don't need to mess with nvidia-prime or Bumblebee). I just tried Manjaro from USB in "nonfree" mode, which loads NVIDIA drivers 370.28 on boot and uses Xorg 1.18.4 and kernel 4.4.x (so same as Ubuntu 16.04) and it works without issues - inxi confirms that the card uses nvidia drivers and it works fine with an external monitor too, which is [the sole reason I want to get the NVIDIA drivers to work]("http://askubuntu.com/questions/866544/16-04-both-screens-turn-black-when-plugging-in-an-external-monitor-to-notebook").

---

