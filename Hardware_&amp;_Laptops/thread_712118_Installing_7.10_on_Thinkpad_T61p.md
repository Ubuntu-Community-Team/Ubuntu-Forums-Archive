---
title: "Installing 7.10 on Thinkpad T61p"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by cmnorton on 2008-03-01
The content of this post mirrors some of [http://ubuntuforums.org/showthread.php?t=696822](http://ubuntuforums.org/showthread.php?t=696822), but I thought it might be helpful to have a series of steps from beginning to end.

I have installed Ubuntu 6.06, 6.10, 7.04, and 7.10 on an Acer Laptop (Travelmate 630) and an Acer Pentium IV (pre-Threaded) desktop. The desktop was purchased about four years ago, but is new enough to have native USB 2.0. 

These installations were simple compared to installing Ubuntu on a T61p, and I believe the advanced NVIDIA graphics is the cause.

1) Using bittorrent, I downloaded a 7.10 live CD image; burned; and checked the CD. 

Then, I preserved the XP environment that was installed on the T61p by making the rescue DVDs; installing Acronis imaging/backup software; and backing up the drive to a SAMBA share.

2) I booted with the live Ubuntu CD. From instinct, I chose start or load Ubuntu in safe mode. This instinct was from having installed on the Acer Travelmate. 

I could not run Ubuntu in safe mode. I got a "black"  during the launch process from the live CD menu. 

3) I rebooted from the live CD, and chose command line installation. This completed successfully, but upon reboot, I still got the black screen.

4) I booted into recovery mode from the grub menu, and ran these commands:

# dhclient eth0 
# aptitude update 
# aptitude upgrade

These completed succssfully, but upon reboot, I still was getting a black screen..

5) Then, I rebooted and selected recovery mode again. I ran dpkg-reconfigure xserver-xorg, and first chose the vesa driver, taking all other defaults. This was not successful. I still got the black screen.

6) I rebooted into recovery mode again, re-ran dpkg-reconfigure xserver-xorg and chose the vga driver.
After reboting, I was able to continue past the low resolution warning, run the restricted drivers manager, and select the nvidia driver; reboot; and all was well.

This tutorial might have ended hapilly here, but this Thinkpad T61p's role is that of portable development workstation. It has 2GB RAM; a dual core CPU; and a large HD. The purpose is to house our three in-house Informix applications. So, it needs to work in a KVM switch environment.

Unfortunately, the advanced 3D graphics prevented working with an external flatscreen monitor alone or part of a KVM switch. 

7) I ran Restricted Drivers Manager; de-selected the nvidia driver; rebooted; told the low-res warning that I wanted to remain in low res; selected a reasonable resolution in the 1280 range; and the external monitor now works fine.

---

