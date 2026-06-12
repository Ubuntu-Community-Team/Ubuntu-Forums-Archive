---
title: "Stuck in Unity 2d - Graphics Card not Recognised"
date: 2012-07-27
forum: Hardware
---

### Post by Craig806 on 2012-07-27
This is my first experience using linux. 

I have a 1.5 year old Samsung laptop that I just installed Ubuntu 12.04 and all available updates.

I am stuck in Ubuntu 2D, when i go to the login screen, i can pick between Ubuntu and Ubuntu 2D but whichever i choose it seems I'm stuck in 2D. I was able to use 3d when I was trying out the Ubuntu disc before installing. 

My Graphics Card is a NVIDIA GeForce 310M
I also have 4gb Ram and an Intel i5 processor

When i go into system settings - details it says:
Graphics unknown
Driver unknown
Experience standard

Any thoughts on how to resolve this?

Is there something else I should be looking at?

---

### Post by carl4926 on 2012-07-27
Open the Additional Drivers
Is it offering the nvidia proprietary driver?

---

### Post by Craig806 on 2012-07-28
It says "no proprietary drivers are in use on this system" and doesn't offer any.

---

### Post by carl4926 on 2012-07-28
Try booting with 'nomodeset' argument - see if that helps.


Or install synaptic and manually add the driver

or

```
sudo apt-get install nvidia-current
```

---

### Post by Craig806 on 2012-07-28
i'm not sure how to perform the first 2 suggestions but i tried entering the code in the terminal and this was the result:

craig@craig-Q430-Q530:~$ sudo apt-get install nvidia-current
[sudo] password for craig: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by carl4926 on 2012-07-28
So it's installed

Take a read
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Did you reboot?


You may need to check that Nouveau is blacklisted (that's what nomodeset does)
You can actually remove it, see the link though

---

### Post by Craig806 on 2012-07-28
Thanks for the help so far, I would be lost without it. 

I rebooted after installing the latest drivers and it still does not recognize the graphics card and i am still stuck in 2D

I followed the link and read the whole page but when i open additional drivers, nothing is available

I tried removing Nouveau and after rebooting, my computer was stuck in 640x480 resolution and the physical keyboard stopped working. 

So i went ahead and just re-installed Ubuntu, ran the updates and i'm back to square one. 

I'm not sure if this is related or significant but in the dash i type in nvidea and open up 'nvidea x server settings' i get the message: You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by carl4926 on 2012-07-28
If you don't install the nvidia driver post install
How does it perform?. Because technically it should be as it was from the CD

---

### Post by Craig806 on 2012-07-28
I have no idea? I'd hate to go back to windows but Ubuntu and my graphics card are not playing nice. :(

i tried the instructions here: [http://blog.musicvm.com/solved-you-do-not-appear-be-using-nvidia-x-driver-linux-ubuntu](http://blog.musicvm.com/solved-you-do-not-appear-be-using-nvidia-x-driver-linux-ubuntu)

......but it didn't work and I am again stuck in 640x480, no 3d, graphics not recognized, no additional drivers, nvidea xserver still giving the same message. (re-installing again...)

Here were the results of my attempt per the instructions in the link: seems like something went wrong toward the end....

craig@craig-Q430-Q530:~$ sudo apt-get --purge remove xserver-xorg-video-nouveau
[sudo] password for craig: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xserver-xorg-video-all* xserver-xorg-video-nouveau*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 400 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 169458 files and directories currently installed.)
Removing xserver-xorg-video-all ...
Removing xserver-xorg-video-nouveau ...
Processing triggers for man-db ...
craig@craig-Q430-Q530:~$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.2.0-27-generic-pae is already the newest version.
linux-headers-3.2.0-27-generic-pae set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
craig@craig-Q430-Q530:~$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
craig@craig-Q430-Q530:~$ sudo update-alternatives --config gl_conf
update-alternatives: error: no alternatives for gl_conf.
craig@craig-Q430-Q530:~$ sudo ldconfig
craig@craig-Q430-Q530:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic-pae
craig@craig-Q430-Q530:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a
                  Driver line.

Backed up file '/etc/X11/xorg.conf' as
'/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by carl4926 on 2012-07-29
Personally I try manually installing the nvidia blob

Since it's depreciated, /etc/X11/xorg.conf
shouldn't even exist

In rare cases users may have to write one of their own

---

