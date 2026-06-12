---
title: "3COM PCMCIA 3crxjk10075 under not detected Ubuntu 8.10"
date: 2008-05-08
forum: Hardware
---

### Post by kirys on 2008-05-08
I've installed ubuntu 8.10 on a laptop, and I was going to use this atheros based card (the madwifi site says that is fully supported) on this laptop.

But Ubuntu doesn't detect the card.

pccard detect the card insertion, but lspci report "Atheros Communication Inc. Unknown device ff96"

also load manually (with modprobe) ath_hal and ath_pci doesn't seem to solve the problem

Do you have any suggestion?
Thank you
Kirys

---

### Post by gabril on 2008-12-04
Hey! I had a similar problem! I have a e620 pcmcia hsdpa modem that was bought due to good compatibility with linux kernels. Now facing the problem of the pcmcia not being detected at all! I started assuming things. And while trying to fix a problem the main thing you Should NOT do is start assuming things! For starters do NOT assume that ubuntu mounts the pcmcia device as a usb serial because this is not the case! Neither as a pci. 

2 days post coming to this conclusion and whilst making myself a baldy (no razors involved!) I came to the conclusion that this is something that is a standing problem in the new ubuntu dist! 

After hours of research i finally came up with a solution to the problem.
Always when looking for a solution you should look into the core, and as we all know ubuntu is a derivative of the opsys debian. So i installed debian (etchn'ahalf) and followed the fist guide i found on google about how to connect with my modem and voila it suddenly works. 

Thus! If you want full pcmcia support, its time to move on! Debian is NOT that hard!
Here follows a brief install guide.

You must have internet to via ethernet for this to work;)! 

[www.debian.com](www.debian.com) download iso of the first cd burn it and lets go!

Follow the install as you did in ubuntu, just when you are asked what additional components you want to install deselect all but the base system and laptop.

you now have a black screen with a big cute terminal!:KS
write:

$ su
$ aptitude update
$ aptitude install xserver-xorg xfce4*(or kde4/3 or gnome 'Whatever')* sudo  gedit abiword wvdail firefox thunderbird gimp fretsonfire wine and quemu gnumerics *and you almost done having a full operating system*
$exit


I.e if you have a nvidia laptop (then rejoice, because i have intel:o) 
just type:

$ su
$ aptitude install xserver-xorg-driver-nvidia*/intel/ati/trident or whatever*
$exit

Now you have to give yourself sudorights!

$ su
$ nano /etc/sudoers
[I]you will there se ROOT All=ALL(ALL)
just over paste "yourloginname" ALL=ALL(ALL) or whatever it says on root
ctrl+o ctrl+x[/I]
$ exit
now you can use sudo instead of su (which is root!)

now just type in the console "startx" and you are on your way!:D

final stepp to success for full hardware acceleration and a good screen mouse and all 
google you laptop make + "**xorg.conf**" and look what to put in there.

the file is in /etc/X11/xorg.conf

so to edit it you type

$ sudo nano /etc/X11/xorg.conf

pm me if anything is unclear! Or delete this post if ubuntu fixed the problem...

---

