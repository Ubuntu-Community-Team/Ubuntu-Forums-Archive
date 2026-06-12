---
title: "kernel updates/driver issues?"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by osakechan on 2009-09-04
Ok, this is really a multi-part question.  The source of many of these complications lies in that I have never been able to get my eth0 to dhcp correctly using any sort of default configuration with a variety of routers.  Since I can't get eth0 to function, I usually fall back to my wireless pci card which was auto-configured on install of 9.04 64bit with the RT2860 module.

Last time there was a kernel update, the driver for my wireless card vanished and I was forced to edit my menu.lst to revert to the previous build to get internet access.  I surmise this has something to do with the need for modules to be compiled against the kernel they are meant to run on?  My working knowledge is not great so I do not know how to do this (or even if i need to).

I have been putting off the latest kernel update because of this reason, and unfortunately I have lately been experiencing a frustratingly high number of crashes with both opera and transmission.  I have therefore resolved to figure out how to update with your help :D

Currently running: 2.6.28-11-generic 64bit

---

### Post by tommcd on 2009-09-05
I don't think a kernel update will fix the problems with Opera and Transmission. The kernel controls drivers, Xorg, HAL, and stuff like that. The kernel does not control applications like Opera and Transmission.
For what it's worth, I use the RT61 driver for my wireless card on my laptop and all is well with that. I am using the latest kernel (2.6.28-15) in Ubuntu 9.04.

What wired network card do you have? Post the output of:
```
lspci | grep -i eth*
```
And also post the output of:
```
lsmod
```
If you do update the kernel and your wireless stops working, run lsmod and make sure the driver for the RT2860 is being loaded.

EDIT: Is the problem with eth0 due to the network card not being properly recognized and configured by Ubuntu? Or is the problem just setting up DHCP with the router? 
What is your setup? Do you go from a DSL or cable modem to a router, and then to the PC? If so, can you get DHCP if you connect the computer directly to the modem without the router?

---

### Post by osakechan on 2009-09-05
Hey, thanks for the reply!  I went ahead with an upgrade last night, now I am greeted with kernel panic very early in the boot process.  Something along the lines of cannot sync: VFS: cant mount root on unknown-block(0,0).

I have a custom kernel separate from the upgrade I installed a while back that is...mostly...working.  For whatever reason with that kernel when i boot, xserver tells me device 0 is busy or something and asks me if i want to boot in low gfx mode, then starts a display on device 1.  I'd revert back to my original kernel, but I'm using a USB keyboard and for whatever reason legacy usb is disabled in my bios so I cant make any pre-boot changes.  I think the easiest thing to do at this point is to scrap the whole installation and start from scratch.

I guess I have a few questions about the kernel upgrade process and the steps I need to take.  How does upgrading the kernel affect currently installed kernel and its modules?  What else does it affect?  What is the best way to clean up and remove old kernels no longer needed after an upgrade?

As for my wired nic, It was installed and working just fine with ubuntu(i cant give you lspci details as I can no longer boot, sorry D:).  Everything would look fine with ifconfig, but no internet.  I tried forcing it using dhclient but it looked like I basically wasn't getting a dhcp response from the router.  I don't think I've tried going directly through the modem, most of my setups involved a router so I will definitely give it a try.  Is there a reason I cannot have both nics up at the same time?  Usually when I have an internet connection with ra0, it dies when I bring up eth0.

EDIT:  About your question in regards to whether or not the wireless driver is being loaded after the upgrade, it definitely isn't.  I tried to load it myself using 'modprobe -i rt2860' and I get an error stating that the module is not found.

---

### Post by tommcd on 2009-09-07
> **osakechan said:**
> I went ahead with an upgrade last night, now I am greeted with kernel panic very early in the boot process.  Something along the lines of cannot sync: VFS: cant mount root on unknown-block(0,0).
Since you have a custom kernel you may need to update your initrd to use with the Ubuntu kernel you installed. See if this allows you to boot with the new standard Ubuntu kernel. Try booting to recovery mode with the new kernel and run:
```

sudo update-initramfs -u -v -k `uname -r`

```
See this:
[https://help.ubuntu.com/community/Update%20the%20Ramdisk](https://help.ubuntu.com/community/Update%20the%20Ramdisk)

To be sure you are updating the initrd for the new kernel, you can replace **`uname -r`** with the exact version number of the kernel. Then try to reboot into the new kernel. Also, be sure that grub's menu.lst has the correct entry for your new kernel.
> **osakechan said:**
> 
I have a custom kernel separate from the upgrade I installed a while back that is...mostly...working...  
I guess I have a few questions about the kernel upgrade process and the steps I need to take.  How does upgrading the kernel affect currently installed kernel and its modules?  What else does it affect?  What is the best way to clean up and remove old kernels no longer needed after an upgrade?
The kernel upgrades in Ubuntu are usually only intended to fix security vulnerabilities, and possibly patch bugs. It is possible that new bugs can be introduced with any kernel upgrade though. Upgrading the kernels that come with the Ubuntu updates is an automatic process. Nothing else usually needs to be done except updating grub for the new kernel. This is also handled automatically by update manager. Or you can edit /boot/grub/menu.lst yourself and add the entry for the new kernel. Ubuntu uses a patched version of the Debian kernels, which are also patched. This makes compiling your own kernel a bit more complicated. Here are some tutorials on compiling a kernel for Ubuntu:
[http://howtoforge.com/roll_a_kernel_debian_ubuntu_way](http://howtoforge.com/roll_a_kernel_debian_ubuntu_way)
[http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html](http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html)
You can get already compiled kernels as ready to install .deb packages for Ubuntu from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

> **osakechan said:**
> 
  Is there a reason I cannot have both nics up at the same time?  Usually when I have an internet connection with ra0, it dies when I bring up eth0.
I think this is because ifconfig will establish an IP address for either the wired or wireless interface, but not both at the same time. I have seen similar behavior with some other distros. 
> **osakechan said:**
> 
EDIT:  About your question in regards to whether or not the wireless driver is being loaded after the upgrade, it definitely isn't.  I tried to load it myself using 'modprobe -i rt2860' and I get an error stating that the module is not found.
Try enabling the backports repo in your sources.list. You can do this in the software sources dialog box. Then install the **linux-backports-modules-jaunty-generic** package. It is possible that updated modules have been provided for your wireless card. It was once recommended to me to install this package in a previous version of Ubuntu in order to keep my RT61 wireless card using the latest driver modules in Ubuntu.

Sorry I took so long to get back. I've been working a lot the last 2 days. Hope some of this stuff helps.

---

