---
title: "Installing an Nvidia proprietary driver manually problem"
date: 2014-04-14
forum: Hardware
---

### Post by cscj01 on 2014-04-14
I am running Ubuntu 12.04.4 with the Gnome Classic shell and have been using the on-board graphics (Intel) from my Gigabyte GA-Z77X_UD5H with no graphics card installed.  Last week I purchased an EVGA Geforce GTX 750 TI graphics card.  Thus began my problems.

According to my research, I had to have the Nvidia driver 334.21.  So I downloaded the driver (.run file), made it executable, purged nvidia*, used Alt-Ctl-F1 to open a terminal session, stopped lightdm, executed the driver install script, and restarted lightdm.  No luck.  It failed because I had no Nvidia card installed (I think).  My first question is why I can't install a driver withour the card installed?

Then, I shut down, installed the card, re-booted, and tried again.  Same problem.

The first error that I see in my install log is ```
 test -e include/generated/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\and
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
   	echo;		
```I am not sure how to go about this to clear up this problem.

The next one is ```
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb, nvidiafb, or nouveau is present and prevents the NVIDIA kernel module from obtaining ownership of the NVIDIA graphics device(s), or no NVIDIA GPU installed in this system is supported by this NVIDIA Linux graphics driver release.
```There is a lot of information in the log file, so I may have missed something.  In any case, would someone help steer me in the right direction.  Thanks.

---

### Post by SeijiSensei on 2014-04-14
Use the "Additional Drivers" application from the System category in the Ubuntu menu.  It will handle all of this for you.

In general, the correct method for installing software on Ubuntu is to use the repositories.  Unless you are installing obscure programs, there is no reason to download software from third-parties.

---

### Post by cscj01 on 2014-04-14
> **SeijiSensei said:**
> Use the "Additional Drivers" application from the System category in the Ubuntu menu.  It will handle all of this for you.

In general, the correct method for installing software on Ubuntu is to use the repositories.  Unless you are installing obscure programs, there is no reason to download software from third-parties.

I actually tried that at first, and my system shows no proprietary drivers available.  My Software Sources has "Proprietary drivers for devices (restricted)" checked.

However, none of the Nvidia drivers in Ubuntu 12.04 support the Geforce GTX 750 TI.

---

### Post by SeijiSensei on 2014-04-14
That's unfortunate!

Maybe this method will work for you: [http://askubuntu.com/questions/425140/unable-toboot-with-nvidia-gtx-750-ti-even-with-latest-beta-drivers](http://askubuntu.com/questions/425140/unable-toboot-with-nvidia-gtx-750-ti-even-with-latest-beta-drivers)

---

### Post by cscj01 on 2014-04-15
> **SeijiSensei said:**
> That's unfortunate!

Maybe this method will work for you: [http://askubuntu.com/questions/425140/unable-toboot-with-nvidia-gtx-750-ti-even-with-latest-beta-drivers](http://askubuntu.com/questions/425140/unable-toboot-with-nvidia-gtx-750-ti-even-with-latest-beta-drivers)

Well, I followed the instructions on the link, and I was able to get the driver generated.  I appreciate you steering me to that link.  Unfortunately, that did not work.

When I booted with my display connected to the Geforce GTX 750 TI, the system booted properly.  I know it booted because I heard the startup sounds.  Problem was, the screen was black except for a band of alternating white and yellow vertical stripes about an inch high across the bottom of the screen.  There was no cursor present, and I could not use any keyboard key combinations (Ctl-Alt-F1, Ctl-Alt-T, etc.) to change things.  So there was no way to accomplish anything.

The link was for someone who had 13.04, so I am wondering if it is possible to get this working on 12.04 at all.  Is there anyone who can comment on this?  If it is true, I can upgrade my release; probably to 14.04 since it will be out Thursday.

---

### Post by Yellow Pasque on 2014-04-15
You have verified that your GTX 750Ti displays BIOS/UEFI screen properly, correct? (I just want to be sure we don't have a defective/DOA card here).

I think the best approach would be to use Ubuntu 14.04 and xorg-edgers PPA: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1287753](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1287753)

---

### Post by bazsound on 2014-04-15
Have you tried this? Beta drivers are for testing purposes, they may not work in all system configurations and most likey have bugs that could make a system that was useable using the open source driver into a non usuable system.

Im not sure how using the most up to the date bleeding edge ubuntu release could help, i wont touch that for atleast a year until they work most of the bugs out. The driver i see on nvidias sight says it supports the 750 and its not beta. reading through the readme states the versions of xorg, kernes etc that shoud work. Based on that it shoud work on 12.04.

> [TABLE]
[TR]
[TH]Software Element[/TH]
[TH]Supported versions[/TH]
[TH]Check With...[/TH]
[/TR]
[TR]
[TD]Linux kernel[/TD]
[TD]2.6.18* and newer[/TD]
[TD]**cat /proc/version**[/TD]
[/TR]
[TR]
[TD]XFree86**[/TD]
[TD]4.0.1 and newer[/TD]
[TD]**XFree86 -version**[/TD]
[/TR]
[TR]
[TD]X.Org**[/TD]
[TD]1.0, 1.1, 1.2, 1.3, 1.4, 1.5, 1.6, 1.7, 1.8, 1.9, 1.10, 1.11, 1.12, 1.13, 1.14, 1.15[/TD]
[TD]**Xorg -version**[/TD]
[/TR]
[TR]
[TD]Kernel modutils[/TD]
[TD]2.1.121 and newer[/TD]
[TD]**insmod --version**[/TD]
[/TR]
[TR]
[TD]glibc[/TD]
[TD]2.0[/TD]
[TD]**ls /lib/libc.so.*** > 6[/TD]
[/TR]
[/TABLE]
*  The NVIDIA Unified Memory kernel module, which is a required component  of the CUDA driver, requires a 2.6.18 or newer kernel. The NVIDIA kernel  supports 2.6.9 and newer kernels, on driver installations which exclude  the Unified Memory kernel module.
** It is only required that you have one of XFree86 or X.Org, not both.
Please see [&#8220;How do I interpret X server version numbers?&#8221;]("http://us.download.nvidia.com/XFree86/Linux-x86_64/334.21/README/faq.html#xversions") for a note about X server version numbers.
If you need to build the NVIDIA kernel module:
[TABLE]
[TR]
[TH]Software Element[/TH]
[TH]Min Requirement[/TH]
[TH]Check With...[/TH]
[/TR]
[TR]
[TD]binutils[/TD]
[TD]2.9.5[/TD]
[TD]**size --version**[/TD]
[/TR]
[TR]
[TD]GNU make[/TD]
[TD]3.77[/TD]
[TD]**make --version**[/TD]
[/TR]
[TR]
[TD]gcc[/TD]
[TD]2.91.66[/TD]
[TD]**gcc --version**[/TD]
[/TR]
[/TABLE]


---

### Post by cscj01 on 2014-04-15
> **Temüjin said:**
> You have verified that your GTX 750Ti displays BIOS/UEFI screen properly, correct? (I just want to be sure we don't have a defective/DOA card here).

I think the best approach would be to use Ubuntu 14.04 and xorg-edgers PPA: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1287753](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1287753)

Yes, the BIOS screen displays properly.

---

### Post by cscj01 on 2014-04-15
> **bazsound said:**
> Have you tried this? Beta drivers are for testing purposes, they may not work in all system configurations and most likey have bugs that could make a system that was useable using the open source driver into a non usuable system.

Im not sure how using the most up to the date bleeding edge ubuntu release could help, i wont touch that for atleast a year until they work most of the bugs out. The driver i see on nvidias sight says it supports the 750 and its not beta. reading through the readme states the versions of xorg, kernes etc that shoud work. Based on that it shoud work on 12.04.

Linux kernel - 3.5.0-48-generic
XFree86 - XFree86 -version gives "command not found"  I found X Protocol is Version 11
X.Org - 1.13.0
Kernel modutils - 3.16
glibc - ls /lib/libc.so.* > 6 gives "cannot access /lib/libc.so.*: No such file or directory" but "sudo aptitude show libc6" gives version 2.13.1

binutils - 2.22
GNU make - 3.81
gcc - 4.6.3

---

### Post by oldfred on 2014-04-15
This says it works:
 Maxwell 750 
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)
All testing happened from an Intel Core i7 4770K "Haswell" system  running Ubuntu 13.10 x86_64 with the Linux 3.12 kernel and Unity 7.1.2 desktop.

---

### Post by cscj01 on 2014-04-15
> **oldfred said:**
> This says it works:
 Maxwell 750 
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)
All testing happened from an Intel Core i7 4770K "Haswell" system  running Ubuntu 13.10 x86_64 with the Linux 3.12 kernel and Unity 7.1.2 desktop.

Well, that says in works in Ubuntu 13.10.  I have Ubuntu 12.04.  However, according to bazsound and his reading of the NVIDIA driver, it should work on 12.04.  I assume he is looking at the same NVIDIA driver I have been trying to get working, 334.21.  That is the NVIDIA current release, and it is not a Beta release.  I have tried to find the information on the NVIDIA site that bazsound posted here, but as yet, I have not found it.  I only know that there is something that is keeping the driver from working for me even though it generates cleanly.  Hopefully someone can spot something in this thread that can unlock the secret.

---

### Post by oldfred on 2014-04-15
I thought 12.04.4 under the hood was very similar to 13.10.
But 14.04 has a lot of kernel, driver & other updates to support the newest hardware.
I might try 14.04.

---

### Post by cscj01 on 2014-04-15
Okay, it's now working, but I'm not sure why.  First a little background.

If I had the EVGA card plugged into the BUS, my Mobo wanted to use it.  I cousudo shutdownld get to the Bios, but could never see the OS.  If the EVGA was not plugged into the BUS, I could use the onboard graphics, but when I generated the driver, I got the weird results reported earlier.  So I thought I would try something radical.  What if I removed the EVGA, booted, then plugged the EVGA into the BUS?  While I never ever do anything such as that, I figured the worst that might happen is I would blow the EVGA and could RMA it.  So, with that in mind, here are my steps.

1. Remove the EVGA
2. Boot to system
3. Plug in the EVGA
3. Open a terminal window with Ctl-Alt-T
4. ```
sudo apt-get purge nvidia*
```
5. ```
sudo apt-get purge xserver-xorg-video-nouveau
```
6. ```
sudo gedit /etc/modprobe.d/blacklist.conf
```
7. Add the following blacklisted items at the end
```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv 
```
8. Save the file
9. ```
sudo gedit /etc/default/grub
```
10. Find```


    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

    and change it to

    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

```11. Save the file
12. ```
sudo update-grub
```
13. Close the terminal
14. Go to text mode terminal with Ctl-Alt-F1
15. Sign in
16. ```
sudo service lightdm stop
```
17. ```
sudo sh ./NVIDIA*
```
18. ```
sudo shutdown
```
19. Unplug display from onboard graphic
20. Plug display into EVGA
21. Reboot

And it works.  Perhaps someone can tell me why the contortions I went through by waiting until after the first Boot to plug the EVGA into the BUS worked.  That is the only step that was different from before.  In any case, as I said, it works.  Perserverence is an amazing thing at times.  Thanks to everyone who responded.  I really believe you all had a hand in my resolving this issue.

---

### Post by oldfred on 2014-04-16
I am not sure I recommend what you have done.

It does not want to install a driver for a card you do not have. So without nVidia card plugged in, it does not let you install a nVidia driver as you do not need it. Not sure that is a good thing or not, but have seen users just try to install nVidia drivers when they do not have nVidia, but saw instructions somewhere.

You should have been able to boot with the nomodeset setting in grub using the nVidia card. You just need to manually change that at grub menu with e, scroll to linux line and replace quiet splash with nomodeset.  Then you can install nVidia driver. Logout and back in and it should work. 

You should not leave nomodeset setting in grub once you have nVidia working.

---

### Post by cscj01 on 2014-04-16
> **oldfred said:**
> I am not sure I recommend what you have done.

It does not want to install a driver for a card you do not have. So without nVidia card plugged in, it does not let you install a nVidia driver as you do not need it. Not sure that is a good thing or not, but have seen users just try to install nVidia drivers when they do not have nVidia, but saw instructions somewhere.

You should have been able to boot with the nomodeset setting in grub using the nVidia card. You just need to manually change that at grub menu with e, scroll to linux line and replace quiet splash with nomodeset.  Then you can install nVidia driver. Logout and back in and it should work. 

You should not leave nomodeset setting in grub once you have nVidia working.

Yes, I did change Grub back to original setting.  And I quite agree with you about what I did.  However, I could not get the Mobo to use anything except the EVGA with it plugged in, so I had to have it unplugged to be able to work.  I had exhausted all options that I knew.  I surely hope to never find myself in that position again.  Thanks for your help and suggestions.

---

