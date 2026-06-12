---
title: "Nvidia driver not loaded"
date: 2019-05-20
forum: Hardware
---

### Post by vippo91 on 2019-05-20
**OK I solved the problem following these instructions:**

$ sudo apt-get remove --purge '^nvidia-.*'
$ sudo apt-get autoremove
$ sudo rm /usr/share/X11/xorg.conf.d/20-intel.conf
$ sudo rm /etc/X11/xorg.conf
$ sudo rm /var/log/Xorg.*
 $sudo apt install nvidia-prime
$ sudo prime-select nvidia
$ grep blacklist /etc/modprobe.d/* | grep nvidia
sudo rm /etc/modprobe.d/blacklist-framebuffer.conf
$ sudo rm /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
$ grep blacklist /lib/modprobe.d/* | grep nvidia
$ sudo rm /lib/modprobe.d/blacklist-nvidia.conf
$ sudo rm /lib/modprobe.d/nvidia-graphics-drivers.conf
$ sudo apt-get install nvidia-driver-430
$ sudo reboot

Hello guys. I am here because I hope that somebody will hopefully help me. I have a laptop with Inte UHD graphics and also Nvidia MX150 graphics.
So during the clean installation of Ubuntu 19.04 I checked that I want to use proprietary graphics driver for my Nvidia graphics card. After the installation I would able to see the Nvidia-settings and open it, but it always tells me that the nvidia driver is not loaded.
[IMG]https://i.imgur.com/5z3VBx2.png[/IMG]

I also tried the installation of the newest 430 driver with disabled secureboot from ppa sources, but unfortunately it is always like this. Yesterday I tried to install the driver from the run package which I downloaded from the Nvidia website, but it fails at DKMS error, so I tried to blacklist the Nvidia Nouveau driver, which I think I succesfully done, but it the result of the installation was the same with DKMS error. 
Now I am really desparated and sad, that an easy task like this is just not working. The Ubuntu always uses my Intel Graphics instead, which is sad because I occasionally play games via Steam....

Anybody here, who can help me figure this out please? Also I am including the Nvidia Bugreport.

---

### Post by hgkrug1 on 2019-05-23
Thanks, this solution at the top worked for me! I have Ubuntu 19.04 installed with a NVIDIA Corporation GP107 [GeForce GTX 1050] card. Not that I fully understand the solution, but it works!

On a freshly installed PC with Ubuntu 18.10, I had to run the following command as well, before I could install the 430 driver: 

sudo add-apt-repository ppa:graphics-drivers/ppa

Unfortunately, I could not reproduce the installation on a freshly installed system.

However, I found a suitable fix at entry #19 of [https://bugs.launchpad.net/gdm/+bug/1798790](https://bugs.launchpad.net/gdm/+bug/1798790)

Try this as a workaround: edit /etc/gdm3/custom.conf 
and uncomment the line: 
#WaylandEnable=false

---

### Post by fely35 on 2019-06-25
Ubuntu 19.04, nvidia-418: The solution for me was to set the primary display in the PC BIOS to Auto, instead of Nvidia. The bios mentioned that if NVIDIA is selected, the Intel GPU is also active. If you don't have that bios option: Nvidia Optimus: [https://wiki.archlinux.org/index.php/NVIDIA_Optimus#Display_Managers](https://wiki.archlinux.org/index.php/NVIDIA_Optimus#Display_Managers)

---

### Post by Agradilius on 2019-06-25
I have 2 dedicated nvidia GFX cards, not a hybrid so I don't use prime or the like. However, after I added that same ppa and tried to install nvidia-driver I too got the same errors. What fixed it for me was to install "xserver-xorg-video-nvidia-430". Again, I'm not on prime, so my fix may or may not help.

Good luck.

---

### Post by dmatos88 on 2019-07-30
[**[COLOR=#000000][/COLOR]**[COLOR=#000000]vippo91, many thanks sir! You saved me a lot of trouble.[/COLOR]]("https://ubuntuforums.org/member.php?u=2125221")

---

