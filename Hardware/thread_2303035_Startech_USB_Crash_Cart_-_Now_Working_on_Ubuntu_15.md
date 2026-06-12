---
title: "Startech USB Crash Cart - Now Working on Ubuntu 15.10 x64"
date: 2015-11-15
forum: Hardware
---

### Post by byb3 on 2015-11-15
This is for any other poor nomads who may face this issue.  Ubuntuforums is well indexed on google so will most likely turn up as the first result as there was only a single other post on reddit.

For people who are not familiar with this product, it's a device that turns your laptop into a KVM and it's pretty damn expensive.  Startech haven't released new software to support the latest Ubuntu so I took it on myself to have a go.  My linux is so-so which is probably why this took so long.  Enjoy!

[http://www.startech.com/uk/Server-Management/KVM-Switches/USB-Crash-Cart-Adapter~NOTECONS02](http://www.startech.com/uk/Server-Management/KVM-Switches/USB-Crash-Cart-Adapter~NOTECONS02)

USB Crash Cart Adapter (Startech)

How to install USB CrashCart software onto Ubuntu 15.10 x64
This took some time, around 6 hours in total some of it productive and a lot of it wasted. It was actually quite easy to get the software loaded, but the software would never see the device. I was looking in completely the wrong place for about 3 hours.
But yes you can get the Startech crash-cart to work on Ubuntu 15.10 x64.
These are the following steps I had to take

Step 1

Install the drivers from the Linux-package64.deb package as provided by Startech. This will extract files to /opt/usb-crash-cart-adapter/. The folder with all the libraries is in the subdirectory 20140415/guts.
Attempt to run it now, and you will most likely get an error regarding libselinux.so.1.

Step 2

Download the libselinux.so.1 from Ubuntu 12.04 distribution. This comes under the package libselinux1. The md5sum for the file I downloaded is:
317e633a53dec5f82142ffa45cbabf77 libselinux.so.1 (md5)
Place this in the folder “20140415/guts”.

Step 3

The version of libstdc++ causes issues and can be replaced with the version used in Ubuntu 15.10. I renamed the file “libstdc++.so.6” to ““libstdc++.so.6.old” and created a symlink:
ln -s /usr/lib/x86_64-linux-gnu/libstdc++.so.6 libstdc++.so.6
0bf3e6694b0ac8edbbe6253edabf1c87 libstdc++.so.6 (md5)

Step 4

I compared a strace on a working version of Ubuntu 12.04. The strace pointed me towards a device being discovered on /dev/DCC_1-4.2.1'. This was also found in the syslog. This wasn't being discovered in Ubuntu 15.10 with an error about the kernel not allowing devices to be renamed. It pointed me towards this file with this error:
Nov 15 22:05:56 medion systemd-udevd[14321]: NAME=“DCC_%k” ignored, kernel device nodes can not be renamed; please fix it in /etc/udev/rules.d/12-dcc2-install.rules:8
The file you edit here may depend on the USB identifier, this is mine (notice the 8463).
Bus 001 Device 046: ID 152a:8463 Thesycon Systemsoftware & Consulting GmbH
I changed it from this:
SUBSYSTEM==“usb”, ACTION==“add”, ENV{DEVTYPE}==“usb_device”, ATTRS{idProduct}==“8463”, ATTRS{idVendor}==“152a”, MODE:=“0666”, NAME:=“DCC_%k”
to this:
SUBSYSTEM==“usb”, ACTION==“add”, ENV{DEVTYPE}==“usb_device”, ATTRS{idProduct}==“8463”, ATTRS{idVendor}==“152a”, MODE:=“0666”, SYMLINK+=“DCC_1-4.2.1”

Step 5

Now after inserted the device, it was finally recognised as /dev/DCC_1-4.2.1 and the software found it as well.

---

### Post by arthusice2 on 2016-06-08
Any luck with 16.04 x86_64?

---

### Post by byb3 on 2016-11-02
Hi,

I have just upgraded my machine to Xubuntu 16.04.1 x64 and I have managed to get the crashcart functioning on this.

To my absolute surprise, there appears to be an updated version of the software available from the Startech website.
[https://www.startech.com/uk/Server-Management/KVM-Switches/USB-Crash-Cart-Adapter~NOTECONS02](https://www.startech.com/uk/Server-Management/KVM-Switches/USB-Crash-Cart-Adapter~NOTECONS02)

It does state in the specifications which I'm sure it didn't before:
[COLOR=#444444][FONT=&amp]Linux 2.6 to 4.4 [/FONT][/COLOR][I]LTS versions only
[/I]
The folder date within the install is now 20150921 which is an update from the previous [COLOR=#000000]20140415.[/COLOR]

It did not work on my first attempt though.  I've worked through the following steps, however I don't know if all of them are required they just worked for me:

1) I've symlinked libstdc++.so.6 in the /opt/usb-crash-cart-adapter/20150921 folder.
lrwxrwxrwx 1 root root       40 Nov  2 23:53 libstdc++.so.6 -> /usr/lib/x86_64-linux-gnu/libstdc++.so.6

2) I've edited the udev rules as the above post.

3) I've added the webupd8 ppa from here ([http://www.ubuntuupdates.org/ppa/webupd8?dist=xenial](http://www.ubuntuupdates.org/ppa/webupd8?dist=xenial)) and installed libwxgtk2.8 packages.  Version 3 is installed by default on 16.04 so both versions of the library are installed:
ii  libwxbase2.8-0:amd64                        2.8.12.1+dfsg2-2ubuntu2+1~webupd8~xenial0     amd64        wxBase library (runtime) - non-GUI support classes of wxWidgets toolkit
ii  libwxbase3.0-0v5:amd64                      3.0.2+dfsg-1.3                                amd64        wxBase library (runtime) - non-GUI support classes of wxWidgets toolkit
ii  libwxgtk2.8-0:amd64                         2.8.12.1+dfsg2-2ubuntu2+1~webupd8~xenial0     amd64        wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)
ii  libwxgtk3.0-0v5:amd64                       3.0.2+dfsg-1.3                                amd64        wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)


4) When the screen came online using Xubuntu 15.10 as a source device, it was discovered as an external monitor with the name "Distributed Management Task Force" (no kidding) so I was seeing the extended monitor through the crashcart which was showing just the wallpaper.  I simply set the display mode to mirror rather than extended and it appears to be working.

I am getting an error box with the following when I load the software first and then connect the crashcart:  (I also get the top line of the video slightly garbled).

Traceback (most recent call last):  File "dover.py", line 470, in SlowTick
  File "dover.py", line 554, in attach
  File "/home/jscobbie/dmtz/20150522/python/adapter.py", line 182, in __init__
  File "/home/jscobbie/dmtz/20150522/python/usbcon/linusb.py", line 449, in getHardwareVersion
AttributeError: device instance has no attribute 'hwver'

If I insert the device first and then run the ./wrapper script this issue seems to disappear.

As a note, the price for a Crashcart on the Startech website has shot up significantly since I bought mine several years ago.  It's showing as £580 on the website which is significantly greater than the £320 I paid.  This can't be put down simply to the recent change in the $/£ exchange rate!

Best Regards,

[FONT=Verdana]
[/FONT]

---

