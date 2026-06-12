---
title: "Wireless, touchpad, and sound have gone, and am unable to identify the real problem"
date: 2013-12-09
forum: Hardware
---

### Post by clustro on 2013-12-09
Hi Ubuntu Forums,

Well, its something of a long story.

It is currently December 9, 2013. I'd say back around January, my /boot partition filled up, and I just never bothered to clean it out to get new updates. I had alot of trouble with a package called "initramfs", which kept getting in the way of software updates. I still haven't fixed initramfs, but I cleaned out the /boot using Synaptic Package Manager, and was able to do a more thorough upgrade/update is still causing this problem,

Now, this past week, I brought my laptop to my office at school. I used it for a bit, then put it in its bag, and eventually the battery died. So, in effect, I restarted my computer.

Today, I opened up my laptop, and the sound, touchpad, and wireless no longer work.

I am not sure where these problems have arisen. Maybe some type of software update was enabled with the restart. Maybe the broken dependencies with initramfs tools is causing the problem. In any case, my laptop is rapidly becoming an expensive, glowing paperweight.

The initramfs situation is something of a catch-22. I try all of the standard commands (sudo apt-get autoclean, sudo apt-get autoremove), but nothing seems to fix or get rid of it for reinstallation. More on that later in the post.

Before my laptop restarted last week, the sound worked, the wireless worked, and the touchpad worked. Now none of them work. The mouse also scrolled at a reasonable rate of speed, but now it only goes super fast. I've been at this for about 2.5 hours, and I'm at my wits end. I don't even know where to begin.

My laptop is a Dell Inspiron 1525.

I'll start with some system output
```
uname -r
```
```
3.2.0-39-generic
```

I tried fixing things myself before coming here. I hoped if I cleaned out /boot, perhaps whatever software update that took place would be "completed", and fix everything back the way it use to be. Using Synaptic Package Manager, I deleted all "linux-image" and "linux-header" prior to my version. I deleted (going from my mental memory here) 31, 32, 33, .., 37 was missing, and 38. I stopped at 39, because well, the internet said it would be bad.


```
lsb_release -a
```
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

```

```
lspci
```
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)


```

This is one thing that is causing me so much headache. Pretty much any help thread concerning the Insprion 1525 is for Broadcom wireless cards. I have an Intel one.

```
iwconfig
```
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

The wireless switch on the right side of the computer is set to the ON position. No activity light is seen when the router is on. I am using my wired connection.

On the issue of sound, I don't know how to check from the Terminal for detecting a sound card. However, when I go to "Sound Settings" in the GUI, all that is listed is a "Dummy output" for my sound output, and both sound tests only produce silence.


Here is outputs related to the initramfs issue. I apologize, because the outputs are rather large.

```
sudo apt-get autoremove -f
```
```
Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following extra packages will be installed:
  initramfs-tools
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
36 not fully installed or removed.
Need to get 0 B/49.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.4.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing apparmor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth:
 plymouth depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing plymouth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lightdm:
 lightdm depends on plymouth (>= 0.8.2-2ubuntu31.1); however:
  Package plymouth is not configured yet.
dpkg: error processing lightdm (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-text:
 plymouth-theme-ubuntu-text depends on plymouth; however:
  Package plymouth is not configured yet.
dpkg: error processing plymouth-theme-ubuntu-text (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth-label:
 plymouth-label depends on plymouth (= 0.8.2-2ubuntu31.1); however:
  Package plymouth is not configured yet.
dpkg: error processing plymouth-label (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-logo:
 plymouth-theme-ubuntu-logo depends on plymouth; however:
  Package plymouth is not configured yet.
 plymouth-theme-ubuntu-logo depends on plymouth-label; however:
  Package plymouth-label is not configured yet.
dpkg: error processing plymouth-theme-ubuntu-logo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuratiNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
on of udev:
 udev depends on initramfs-tools (>= 0.92bubuntu63); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of checkbox:
 checkbox depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing checkbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of checkbox-gtk:
 checkbox-gtk depends on checkbox (>= 0.13.10); however:
  Package checkbox is not configured yet.
dpkg: error processing checkbox-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsolid4: No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already

 libsolid4 depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing libsolid4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkio5:
 libkio5 depends on libsolid4 (= 4:4.8.5-0ubuntu0.2); however:
  Package libsolid4 is not configured yet.
dpkg: error processing libkio5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkparts4:
 libkparts4 depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkparts4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdewebkit5:
 libkdewebkit5 depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
 libkdewebkit5 depends on libkparts4 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkparts4 is not configured yet.
dpkg: error processing libkdewebNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
kit5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkemoticons4:
 libkemoticons4 depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
dpkg: error processing libkemoticons4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkfile4:
 libkfile4 depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
 libkfile4 depends on libsolid4 (= 4:4.8.5-0ubuntu0.2); however:
  Package libsolid4 is not configured yet.
dpkg: error processing libkfile4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libktexteditor4:
 libktexteditor4 depends on libkparts4 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkparts4 is not configured yet.
dpkg: error processing libktexteditor4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkhtml5:
 libkhtml5 depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
 libkhtml5 depends on libkparts4 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkparts4 is not configured yet.
 libkhtml5 depends on libktexteditor4 (= 4:4.8.5-0ubuntu0.2); however:
  Package libktexteditor4 is not configured yet.
dpkg: error processing libkhtml5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkmediaplayer4:
 libkmediaplayer4 depends on libkparts4 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkparts4 is not configured yet.
dpkg: error processing libkmediaplayer4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libknewstuff3-4:
 libknewstuff3-4 depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
dpkg: error processing libknewstuff3-4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libknotifyconfig4:
 libknotifyconfig4 depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
dpkg: error processing libknotifyconfig4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libplasma3:
 libplasma3 depends on libkdewebkit5 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkdewebkit5 is not configured yet.
 libplasma3 depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
 libplasma3 depends on libknewstuff3-4 (= 4:4.8.5-0ubuntu0.2); however:
  Package libknewstuff3-4 is not configured yet.
 libplasma3 depends on libsolid4 (= 4:4.8.5-0ubuntu0.2); however:
  Package libsolid4 is not configured yet.
dpkg: error processing libplasma3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkde3support4:
 libkde3support4 depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
 libkde3support4 depends on libkparts4 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkparts4 is not configured yet.
dpkg: error processing libkde3support4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdoctools:
 kdoctools depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
dpkg: error processing kdoctools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs-bin:
 kdelibs-bin depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
dpkg: error processing kdelibs-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs5-plugins:
 kdelibs5-plugins depends on libkde3support4 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkde3support4 is not configured yet.
 kdelibs5-plugins depends on libkdewebkit5 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkdewebkit5 is not configured yet.
 kdelibs5-plugins depends on libkemoticons4 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkemoticons4 is not configured yet.
 kdelibs5-plugins depends on libkfile4 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkfile4 is not configured yet.
 kdelibs5-plugins depends on libkhtml5 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkhtml5 is not configured yet.
 kdelibs5-plugins depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
 kdelibs5-plugins depends on libkparts4 (= 4:4.8.5-0ubuntu0.2); however:
  Package libkparts4 is not configured yet.
 kdelibs5-plugins depends on libsolid4 (= 4:4.8.5-0ubuntu0.2); however:
  Package libsolid4 is not configured yet.
 kdelibs5-plugins depends on kdoctools (= 4:4.8.5-0ubuntu0.2); however:
  Package kdoctools is not configured yet.
 kdelibs5-plugins depends on kdelibs-bin (= 4:4.8.5-0ubuntu0.2); however:
  Package kdelibs-bin is not configured yet.
dpkg: error processing kdelibs5-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-scriptengine-javascript:
 plasma-scriptengine-javascript depends on libkio5 (>= 4:4.8.1); however:
  Package libkio5 is not configured yet.
 plasma-scriptengine-javascript depends on libplasma3 (>= 4:4.8.1); however:
  Package libplasma3 is not configured yet.
dpkg: error processing plasma-scriptengine-javascript (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-runtime:
 kde-runtime depends on libkdewebkit5 (>= 4:4.8.1); however:
  Package libkdewebkit5 is not configured yet.
 kde-runtime depends on libkemoticons4 (>= 4:4.8.1); however:
  Package libkemoticons4 is not configured yet.
 kde-runtime depends on libkfile4 (>= 4:4.8.1); however:
  Package libkfile4 is not configured yet.
 kde-runtime depends on libkhtml5 (>= 4:4.8.1); however:
  Package libkhtml5 is not configured yet.
 kde-runtime depends on libkio5 (>= 4:4.8.1); however:
  Package libkio5 is not configured yet.
 kde-runtime depends on libkmediaplayer4 (>= 4:4.8.1); however:
  Package libkmediaplayer4 is not configured yet.
 kde-runtime depends on libknewstuff3-4 (>= 4:4.8.1); however:
  Package libknewstuff3-4 is not configured yet.
 kde-runtime depends on libknotifyconfig4 (>= 4:4.8.1); however:
  Package libknotifyconfig4 is not configured yet.
 kde-runtime depends on libkparts4 (>= 4:4.8.1); however:
  Package libkparts4 is not configured yet.
 kde-runtime depends on libplasma3 (>= 4:4.8.1); however:
  Package libplasma3 is not configured yet.
 kde-runtime depends on libsolid4 (>= 4:4.8.1); however:
  Package libsolid4 is not configured yet.
 kde-runtime depends on kdelibs5-plugins (>= 4:4.8.1); however:
  Package kdelibs5-plugins is not configured yet.
 kde-runtime depends on plasma-scriptengine-javascript (= 4:4.8.5-0ubuntu0.2); however:
  Package plasma-scriptengine-javascript is not configured yet.
dpkg: error processing kde-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-runtime:
 kdebase-runtime depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
dpkg: error processing kdebase-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of khelpcenter4:
 khelpcenter4 depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 khelpcenter4 depends on libkhtml5 (>= 4:4.8.1); however:
  Package libkhtml5 is not configured yet.
 khelpcenter4 depends on libkio5 (>= 4:4.8.1); however:
  Package libkio5 is not configured yet.
 khelpcenter4 depends on libkparts4 (>= 4:4.8.1); however:
  Package libkparts4 is not configured yet.
dpkg: error processing khelpcenter4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.9.4); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of upower:
 upower depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing upower (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on udev (>= 149); however:
  Package udev is not configured yet.
dpkg: error processing xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of xserver-xorg-video-intel:
 xserver-xorg-video-intel depends on xorg-video-abi-11; however:
  Package xorg-video-abi-11 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-11 is not configured yet.
 xserver-xorg-video-intel depends on xserver-xorg-core (>= 2:1.10.99.901); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-intel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-openchrome:
 xserver-xorg-video-openchrome depends on xorg-video-abi-11; however:
  Package xorg-video-abi-11 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-11 is not configured yet.
 xserver-xorg-video-openchrome depends on xserver-xorg-core (>= 2:1.10.99.901); however:
  Package xserver-xorg-core is not configured yet.
dpkg: error processing xserver-xorg-video-openchrome (--configure):
 depeNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
ndency problems - leaving unconfigured
Errors were encountered while processing:
 initramfs-tools
 apparmor
 plymouth
 lightdm
 plymouth-theme-ubuntu-text
 plymouth-label
 plymouth-theme-ubuntu-logo
 udev
 network-manager
 checkbox
 checkbox-gtk
 libsolid4
 libkio5
 libkparts4
 libkdewebkit5
 libkemoticons4
 libkfile4
 libktexteditor4
 libkhtml5
 libkmediaplayer4
 libknewstuff3-4
 libknotifyconfig4
 libplasma3
 libkde3support4
 kdoctools
 kdelibs-bin
 kdelibs5-plugins
 plasma-scriptengine-javascript
 kde-runtime
 kdebase-runtime
 khelpcenter4
 network-manager-gnome
 upower
 xserver-xorg-core
 xserver-xorg-video-intel
 xserver-xorg-video-openchrome
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What on earth does it mean when it says:
```
Need to get 0 B/49.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
```?

Is the file really less than a byte? Or is there some error with the repository?

As I said before, I have also used the graphical Synaptic Package Manager to try and fix the initramfs problem. I don't know how to post pictures here, so I will just describe it. When the program first opens, it says "You have 1 broken package, use the Broken Filter to locate it!"

I click on the left list item named "Broken dependencies"

There is one package listed, called "initramfs-tools"

To the left of it is a small ubuntu icon, and to the left of that icon is a white exclamation mark in a red box.
It says "Installed version 0.99ubuntu13.1", and "Latest Version 0.99ubuntu13.4"

(The highly informative description box says the program is "tools for generating an initramfs".)

I right click on the package, and choose "Mark for Upgrade", the click the green "Apply" checkmark icon at the top.
There is another package that needs upgrading though, so instead I go to "Mark all Upgrades", and click "Apply" again.

The details from the box that appears are:

```
initramfs-tools (version 0.99ubuntu13.1) will be upgraded to version 0.99ubuntu13.4
xserver-xorg-core (version 2:1.11.4-0ubuntu10.13) will be upgraded to version 2:1.11.4-0ubuntu10.14

```

I then click "Apply"

"An error has occurred"

```
E: initramfs-tools: dependency problems - leaving unconfigured
E: apparmor: dependency problems - leaving unconfigured
E: plymouth: dependency problems - leaving unconfigured
E: lightdm: dependency problems - leaving unconfigured
E: plymouth-theme-ubuntu-text: dependency problems - leaving unconfigured
E: plymouth-label: dependency problems - leaving unconfigured
E: plymouth-theme-ubuntu-logo: dependency problems - leaving unconfigured
E: udev: dependency problems - leaving unconfigured
E: network-manager: dependency problems - leaving unconfigured
E: checkbox: dependency problems - leaving unconfigured
E: checkbox-gtk: dependency problems - leaving unconfigured
E: libsolid4: dependency problems - leaving unconfigured
E: libkio5: dependency problems - leaving unconfigured
E: libkparts4: dependency problems - leaving unconfigured
E: libkdewebkit5: dependency problems - leaving unconfigured
E: libkemoticons4: dependency problems - leaving unconfigured
E: libkfile4: dependency problems - leaving unconfigured
E: libktexteditor4: dependency problems - leaving unconfigured
E: libkhtml5: dependency problems - leaving unconfigured
E: libkmediaplayer4: dependency problems - leaving unconfigured
E: libknewstuff3-4: dependency problems - leaving unconfigured
E: libknotifyconfig4: dependency problems - leaving unconfigured
E: libplasma3: dependency problems - leaving unconfigured
E: libkde3support4: dependency problems - leaving unconfigured
E: kdoctools: dependency problems - leaving unconfigured
E: kdelibs-bin: dependency problems - leaving unconfigured
E: kdelibs5-plugins: dependency problems - leaving unconfigured
E: plasma-scriptengine-javascript: dependency problems - leaving unconfigured
E: kde-runtime: dependency problems - leaving unconfigured
E: kdebase-runtime: dependency problems - leaving unconfigured
E: khelpcenter4: dependency problems - leaving unconfigured
E: network-manager-gnome: dependency problems - leaving unconfigured
E: upower: dependency problems - leaving unconfigured
E: xserver-xorg-core: dependency problems - leaving unconfigured
E: xserver-xorg-video-intel: dependency problems - leaving unconfigured
E: xserver-xorg-video-openchrome: dependency problems - leaving unconfigured

```

So really, I am at a loss as to how to fix the problems with my laptop.

I guess the key questions that would help me to proceed are:

1. Is initramfs a critical package, or can it be deleted/removed?
2. Why are all of these other packages popping up in the error related to initramfs? Like upower?
3. Does initramfs or xserver-xorg-core cause wireless, touchpad, or sound problems?
4. Am I going in the totally wrong direction? Is initramfs and xserver-xorg-core unrelated to these problems?
5. If so... what is the fix? I wish I could be of more help, but I really just don't know why these problems just sprouted up all of the sudden.

Any help that is offered is highly, highly appreciated.

---

### Post by clustro on 2013-12-09
Really can use some help on this. Please. Any help is appreciated.

---

### Post by clustro on 2013-12-10
Well, in the time it took me to author that huge post yesterday, I just decided to get rid of Linux and install windows vista.

Now everything works again.

---

### Post by codenine75a on 2013-12-10
no touchie initramfs.  Try reinstalling your kernel by using the deb packager.  It will get your core drivers back.

---

